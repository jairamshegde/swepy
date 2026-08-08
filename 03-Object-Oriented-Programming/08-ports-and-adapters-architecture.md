# Ports and Adapters Architecture (Hexagonal Architecture) in Python 🔌

> **From OOP Fundamentals to Professional Architecture**: How Abstraction, Polymorphism, Composition, Dependency Inversion, and Dataclasses power clean software design.

---

## 📌 Sequence Navigation

This guide is part of the **Python Object-Oriented Programming (OOP) Series**:

1. [01-oops-part-1-introduction.md](./01-oops-part-1-introduction.md) — Procedural vs. OOP Intro
2. [02-oops-four-pillars.md](./02-oops-four-pillars.md) — The Four Pillars of OOP
3. [03-oops-part-2-zero2hero.md](./03-oops-part-2-zero2hero.md) — OOP Foundations, Methods & Inheritance
4. [04-dunder-methods-getters-setters.md](./04-dunder-methods-getters-setters.md) — Dunder Methods & Getters/Setters
5. [05-oops-part-3-zero2hero.md](./05-oops-part-3-zero2hero.md) — Advanced OOP (Composition, Context Managers, Generators)
6. [06-dataclasses-intuitive-guide.md](./06-dataclasses-intuitive-guide.md) — Dataclasses & Boilerplate Elimination
7. [07-design-patterns-notes.md](./07-design-patterns-notes.md) — Design Patterns in Python
8. **08-ports-and-adapters-architecture.md** 👈 *(Current Document)* — Ports & Adapters Architecture in Python

---

## Table of Contents
- [1. What is Ports & Adapters Architecture?](#1-what-is-ports--adapters-architecture)
  - [1.1 The Electrical Wall Socket Analogy](#11-the-electrical-wall-socket-analogy)
  - [1.2 The Hexagonal Architecture Layers](#12-the-hexagonal-architecture-layers)
- [2. Master List of OOP Concepts Used](#2-master-list-of-oop-concepts-used)
- [3. Deep-Dive: Linking OOP Concepts to Architecture](#3-deep-dive-linking-oop-concepts-to-architecture)
  - [3.1 Abstraction (`ABC`) = Defining the Ports](#31-abstraction-abc--defining-the-ports)
  - [3.2 Polymorphism = Interchangeable Adapters](#32-polymorphism--interchangeable-adapters)
  - [3.3 Composition (HAS-A) = Assembling the Service](#33-composition-has-a--assembling-the-service)
  - [3.4 Dependency Inversion Principle (DIP) = Reversing Control](#34-dependency-inversion-principle-dip--reversing-control)
  - [3.5 Encapsulation = Protecting Core Business Logic](#35-encapsulation--protecting-core-business-logic)
  - [3.6 Dataclasses = Pure Technology-Agnostic Entities](#36-dataclasses--pure-technology-agnostic-entities)
- [4. Complete Code Walkthrough (Text Processing Domain)](#4-complete-code-walkthrough-text-processing-domain)
- [5. Why Senior Engineers Use This Pattern](#5-why-senior-engineers-use-this-pattern)

---

## 1. What is Ports & Adapters Architecture?

**Ports and Adapters Architecture** (also known as **Hexagonal Architecture** or **Clean Architecture**) is a software design pattern created by Alistair Cockburn.

Its primary goal is to **isolate your core business logic** from external technologies like databases (Postgres, MongoDB), web frameworks (FastAPI, Flask), cloud providers (AWS S3, GCP), or external APIs.

---

### 1.1 The Electrical Wall Socket Analogy

Think of your core business logic like a laptop running on electricity:

- **The Port (Wall Socket):** Standardized electrical outlet. It dictates *what* power interface is required (e.g., 110V/220V AC).
- **The Adapter (Power Cable Plug):** Fits into the wall socket on one side and converts power for your laptop on the other side.
- **The Result:** You can plug your laptop into a wall socket in the US, Europe, or an airplane using different adapters — **without modifying your laptop's internal motherboard!**

```text
  [ External World ]          [ Boundaries ]           [ Core Domain ]
┌────────────────────┐     ┌─────────────────┐     ┌─────────────────────┐
│  Local FileSystem  │ ──> │                 │     │                     │
├────────────────────┤     │  DocumentReader │ ──> │ TextProcessing      │
│  AWS S3 Bucket     │ ──> │     (Port)      │     │     Service         │
├────────────────────┤     └─────────────────┘     │  (Pure Business     │
│  PostgreSQL DB     │ ──> │                 │     │      Logic)         │
└────────────────────┘     └─────────────────┘     └─────────────────────┘
     (Adapters)                  (Ports)               (Inside Core)
```

---

### 1.2 The Hexagonal Architecture Layers

1. **Inside (The Core Domain):** Pure Python business rules, data transformations, and domain models. Zero dependencies on external frameworks or database libraries.
2. **Ports (The Interfaces):** Abstract Base Classes (`ABC`) defined *by the core* that declare expected inputs and outputs.
3. **Adapters (The Infrastructure):** Concrete classes that implement the Ports to communicate with real databases, file systems, or APIs.

---

## 2. Master List of OOP Concepts Used

Ports and Adapters is not a magic trick — it is built by orchestrating 6 core OOP concepts:

| OOP Concept | Architectural Role in Ports & Adapters | Python Mechanism |
| :--- | :--- | :--- |
| **1. Abstraction** | Declares the **Ports** (contracts specifying what operations must exist). | `ABC` and `@abstractmethod` |
| **2. Polymorphism** | Enables **Adapters** to be swapped dynamically at runtime without changing the core. | Duck typing / Subclass method overrides |
| **3. Composition** | Embeds Port contracts inside the Domain Service (**HAS-A** relationship). | `self.reader = reader_port` in `__init__` |
| **4. Dependency Inversion (DIP)** | High-level business logic depends on Abstract Ports, not low-level Database details. | Dependency Injection via `__init__` |
| **5. Encapsulation** | Shields pure text processing logic inside protective method boundaries. | Private/Protected attributes & methods |
| **6. Dataclasses** | Defines pure, technology-agnostic **Domain Entities** & Data Transfer Objects (DTOs). | `@dataclass` |

---

## 3. Deep-Dive: Linking OOP Concepts to Architecture

---

### 3.1 Abstraction (`ABC`) = Defining the Ports

In OOP, **Abstraction** hides complex mechanics behind a clean interface. In Ports & Adapters, **a Port IS an Abstract Class**.

The domain core defines what it needs from the outside world without caring how it is implemented:

```python
from abc import ABC, abstractmethod
from dataclasses import dataclass

@dataclass
class TextDocument:
    doc_id: str
    content: str

# 🔌 OUTBOUND PORT (Defined BY the core domain)
class DocumentReaderPort(ABC):
    @abstractmethod
    def read_document(self, doc_id: str) -> TextDocument:
        """Abstract contract: Any adapter MUST implement this method signature"""
        pass
```

---

### 3.2 Polymorphism = Interchangeable Adapters

In OOP, **Polymorphism** allows calling the same method signature across different classes. In Ports & Adapters, **Adapters ARE polymorphic implementations of Ports**.

Whether reading from a local disk, AWS S3, or a mock testing dictionary, every Adapter implements `.read_document()`:

```python
# 🔌 ADAPTER 1: Local Disk Reader
class LocalFileAdapter(DocumentReaderPort):
    def read_document(self, doc_id: str) -> TextDocument:
        with open(f"./data/{doc_id}.txt", 'r') as f:
            return TextDocument(doc_id=doc_id, content=f.read())

# 🔌 ADAPTER 2: Cloud S3 Reader
class S3StorageAdapter(DocumentReaderPort):
    def read_document(self, doc_id: str) -> TextDocument:
        # Pretend AWS boto3 fetch occurs here
        s3_content = f"S3 Cloud Content for {doc_id}"
        return TextDocument(doc_id=doc_id, content=s3_content)

# 🔌 ADAPTER 3: In-Memory Mock Reader (For Instant Unit Tests!)
class MockMemoryAdapter(DocumentReaderPort):
    def __init__(self, sample_data: dict):
        self.sample_data = sample_data
        
    def read_document(self, doc_id: str) -> TextDocument:
        return TextDocument(doc_id=doc_id, content=self.sample_data.get(doc_id, ""))
```

---

### 3.3 Composition (HAS-A) = Assembling the Service

Instead of inheriting from database classes, the Domain Service uses **Composition**. The service **HAS-A** reader port and **HAS-A** repository port:

```python
class TextProcessingService:
    def __init__(self, reader: DocumentReaderPort):
        # COMPOSITION: The domain service HAS-A DocumentReaderPort
        self.reader = reader
```

---

### 3.4 Dependency Inversion Principle (DIP) = Reversing Control

In traditional procedural code:
- `Business Logic` ──> `Imports PostgreSQL Library` (High level depends on Low level)

With **Dependency Inversion (DIP)**:
- `Business Logic` ──> `Depends on Abstract Port (ABC)`
- `PostgreSQL Adapter` ──> `Implements Abstract Port (ABC)`

Both depend on the abstraction! We inject the concrete adapter into `__init__`:

```python
# DEPENDENCY INJECTION: Passing concrete adapters into constructor
reader_adapter = S3StorageAdapter()
service = TextProcessingService(reader=reader_adapter)  # Injected!
```

---

### 3.5 Encapsulation = Protecting Core Business Logic

The core service encapsulates domain rules (quality rules, stop-word removal, frequency counts) so external database code can never alter business rules.

```python
class TextProcessingService:
    def __init__(self, reader: DocumentReaderPort):
        self.reader = reader
        
    def process_and_analyze(self, doc_id: str) -> dict:
        # Encapsulated Business Rule
        document = self.reader.read_document(doc_id)
        words = document.content.lower().split()
        return {"doc_id": doc_id, "word_count": len(words)}
```

---

### 3.6 Dataclasses = Pure Technology-Agnostic Entities

We use `@dataclass` to model pure domain data entities (`TextDocument`, `AnalysisResult`). They contain no SQL decorators, no ORM metadata, and no web framework code.

```python
@dataclass(frozen=True)
class AnalysisResult:
    doc_id: str
    total_words: int
    unique_words: int
```

---

## 4. Complete Code Walkthrough (Text Processing Domain)

Here is a complete, runnable example bringing **Ports & Adapters** together with our **Text Processing** domain:

```python
from abc import ABC, abstractmethod
from dataclasses import dataclass, field
import string

# ======================================================
# 1. DOMAIN ENTITY (Pure Dataclass)
# ======================================================
@dataclass
class TextDocument:
    doc_id: str
    raw_text: str

@dataclass(frozen=True)
class AnalysisSummary:
    doc_id: str
    word_count: int
    top_words: list

# ======================================================
# 2. OUTBOUND PORTS (Abstract Base Classes)
# ======================================================
class DocumentReaderPort(ABC):
    @abstractmethod
    def fetch_document(self, doc_id: str) -> TextDocument:
        pass

class DocumentWriterPort(ABC):
    @abstractmethod
    def save_summary(self, summary: AnalysisSummary) -> bool:
        pass

# ======================================================
# 3. CORE DOMAIN SERVICE (Encapsulation + Composition)
# ======================================================
class TextProcessingService:
    def __init__(self, reader: DocumentReaderPort, writer: DocumentWriterPort):
        # Composition + Dependency Injection
        self.reader = reader
        self.writer = writer

    def execute_pipeline(self, doc_id: str) -> AnalysisSummary:
        # Pure Business Logic (No SQL, No HTTP, No Cloud SDKs!)
        doc = self.reader.fetch_document(doc_id)
        
        # Text cleaning and word count calculation
        clean_text = doc.raw_text.translate(str.maketrans('', '', string.punctuation)).lower()
        words = clean_text.split()
        
        # Calculate top words
        word_freq = {}
        for w in words:
            word_freq[w] = word_freq.get(w, 0) + 1
        sorted_words = sorted(word_freq.items(), key=lambda x: x[1], reverse=True)[:3]
        
        summary = AnalysisSummary(
            doc_id=doc_id,
            word_count=len(words),
            top_words=[w[0] for w in sorted_words]
        )
        
        # Save output via writer port
        self.writer.save_summary(summary)
        return summary

# ======================================================
# 4. ADAPTERS (Concrete Infrastructure Implementations)
# ======================================================
# Adapter A: Local Disk Reader
class LocalFileAdapter(DocumentReaderPort):
    def fetch_document(self, doc_id: str) -> TextDocument:
        print(f"📂 [LocalFileAdapter] Reading {doc_id} from disk...")
        return TextDocument(doc_id=doc_id, raw_text="Natural language processing with Python OOP is clean!")

# Adapter B: AWS S3 Cloud Reader
class S3CloudAdapter(DocumentReaderPort):
    def fetch_document(self, doc_id: str) -> TextDocument:
        print(f"☁️ [S3CloudAdapter] Fetching s3://my-bucket/{doc_id}.txt...")
        return TextDocument(doc_id=doc_id, raw_text="Cloud storage text data stream loaded successfully.")

# Adapter C: Console Log Writer
class ConsoleWriterAdapter(DocumentWriterPort):
    def save_summary(self, summary: AnalysisSummary) -> bool:
        print(f"💾 [ConsoleWriterAdapter] Exported Summary: {summary}")
        return True

# ======================================================
# 5. RUNTIME ASSEMBLY (Swapping Adapters Frictionlessly!)
# ======================================================
if __name__ == "__main__":
    console_writer = ConsoleWriterAdapter()
    
    print("--- RUNNING WITH LOCAL FILE ADAPTER ---")
    local_reader = LocalFileAdapter()
    service1 = TextProcessingService(reader=local_reader, writer=console_writer)
    service1.execute_pipeline("doc_101")

    print("\n--- SWAPPING TO S3 CLOUD ADAPTER (Zero Core Code Changes!) ---")
    s3_reader = S3CloudAdapter()
    service2 = TextProcessingService(reader=s3_reader, writer=console_writer)
    service2.execute_pipeline("doc_202")
```

---

## 5. Why Senior Engineers Use This Pattern

| Benefit | How OOP Powers It | Practical Impact |
| :--- | :--- | :--- |
| **1. 100% Testable Core** | **Polymorphism & Abstraction** | Pass a `MockMemoryAdapter` into unit tests. Tests run in 5 milliseconds without spinning up Docker or Postgres! |
| **2. Zero Infrastructure Lock-in** | **Dependency Inversion** | Switch from AWS S3 to Google Cloud Storage by creating a new Adapter class. The core domain code remains completely untouched. |
| **3. Parallel Teamwork** | **Abstract Ports** | Team Member A builds the `FastAPI` web adapter; Team Member B builds the `Postgres` database adapter; Team Member C builds the Core Business Rules simultaneously! |
| **4. Long-Term Maintainability** | **Encapsulation & Composition** | Framework upgrades (e.g. updating Pydantic or SQLAlchemy) only touch adapter files, leaving business logic completely stable. |

---

> **The Architectural Mindset:**  
> *"Build your core application logic inside a protective fortress of Abstract Ports. Connect database drivers, web frameworks, and cloud SDKs as external, pluggable Adapters."*
