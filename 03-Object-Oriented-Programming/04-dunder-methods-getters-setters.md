# Dunder Methods & Getters/Setters in Python 🪄

> **Mastering Pythonic Object Customization**: How double-underscore magic methods and `@property` decorators transform standard Python classes into intuitive, robust objects.

---

## 📌 Sequence Navigation

This guide is part of the **Python Object-Oriented Programming (OOP) Series**:

1. [01-oops-part-1-introduction.md](./01-oops-part-1-introduction.md) — Procedural vs. OOP Intro
2. [02-oops-four-pillars.md](./02-oops-four-pillars.md) — The Four Pillars of OOP
3. [03-oops-part-2-zero2hero.md](./03-oops-part-2-zero2hero.md) — OOP Foundations, Methods & Inheritance
4. **04-dunder-methods-getters-setters.md** 👈 *(Current Document)* — Dunder Methods & Getters/Setters
5. [05-oops-part-3-zero2hero.md](./05-oops-part-3-zero2hero.md) — Advanced OOP (Composition, Context Managers, Generators)
6. [06-dataclasses-intuitive-guide.md](./06-dataclasses-intuitive-guide.md) — Dataclasses & Boilerplate Elimination
7. [07-design-patterns-notes.md](./07-design-patterns-notes.md) — Design Patterns in Python
8. [08-ports-and-adapters-architecture.md](./08-ports-and-adapters-architecture.md) — Ports & Adapters Architecture in Python

---

## Table of Contents
- [1. What Are Dunder Methods?](#1-what-are-dunder-methods)
- [2. Essential Dunder Methods in Action](#2-essential-dunder-methods-in-action)
  - [2.1 Object Initialization & Representation (`__init__`, `__str__`, `__repr__`)](#21-object-initialization--representation-__init__-__str__-__repr__)
  - [2.2 Sequence & Container Protocols (`__len__`, `__getitem__`, `__contains__`)](#22-sequence--container-protocols-__len__-__getitem__-__contains__)
  - [2.3 Comparison Protocols (`__eq__`, `__lt__`)](#23-comparison-protocols-__eq__-__lt__)
  - [2.4 Callable Objects (`__call__`)](#24-callable-objects-__call__)
- [3. Getters and Setters: Why & When to Use Them](#3-getters-and-setters-why--when-to-use-them)
  - [3.1 The Problem with Direct Attribute Access](#31-the-problem-with-direct-attribute-access)
  - [3.2 The Traditional (Non-Pythonic) Getter/Setter Trap](#32-the-traditional-non-pythonic-gettersetter-trap)
  - [3.3 The Pythonic Solution: `@property` Decorator](#33-the-pythonic-solution-property-decorator)
  - [3.4 Computed & Read-Only Attributes](#34-computed--read-only-attributes)
- [4. Summary Matrix: Dunder Methods & Properties](#4-summary-matrix-dunder-methods--properties)

---

## 1. What Are Dunder Methods?

**"Dunder"** is short for **D**ouble **Under**score (`__name__`). In Python, dunder methods (also known as **Magic Methods**) are special predefined methods surrounded by double underscores.

### The Core Principle
Python does not use special keywords for built-in operations (like `len()`, `print()`, `==`, `+`, `in`, or indexing `[]`). Instead, **Python delegates built-in operations to dunder methods under the hood**:

```text
Built-in Operation              Python Execution Under the Hood
──────────────────              ───────────────────────────────
print(doc)              ───>    doc.__str__()
len(doc)                ───>    doc.__len__()
"python" in doc         ───>    doc.__contains__("python")
doc[0]                  ───>    doc.__getitem__(0)
doc1 == doc2            ───>    doc1.__eq__(doc2)
doc()                   ───>    doc.__call__()
```

---

## 2. Essential Dunder Methods in Action

Let's explore how dunder methods enable custom objects to seamlessly integrate with native Python features using our **Text Processing** domain.

---

### 2.1 Object Initialization & Representation (`__init__`, `__str__`, `__repr__`)

- `__init__`: Constructor method called when instantiating an object.
- `__str__`: User-facing informal string output (used by `print()` and `str()`).
- `__repr__`: Developer-facing unambiguous string representation (used in interactive shells and debugging).

```python
class TextDocument:
    def __init__(self, filename: str, content: str):
        self.filename = filename
        self.content = content
        
    def __str__(self) -> str:
        """User-friendly print output"""
        return f"📄 Document '{self.filename}' ({len(self.content)} characters)"
        
    def __repr__(self) -> str:
        """Developer debugging representation"""
        return f"TextDocument(filename={self.filename!r}, content_len={len(self.content)})"

doc = TextDocument("sample.txt", "Natural Language Processing with Python")

print(str(doc))   # 📄 Document 'sample.txt' (39 characters)
print(repr(doc))  # TextDocument(filename='sample.txt', content_len=39)
```

---

### 2.2 Sequence & Container Protocols (`__len__`, `__getitem__`, `__contains__`)

By implementing these dunder methods, your custom object behaves like a native Python list or string container!

```python
class TextBatch:
    def __init__(self, documents: list):
        self.documents = documents  # List of TextDocument instances
        
    def __len__(self) -> int:
        """Enables len(batch)"""
        return len(self.documents)
        
    def __getitem__(self, index: int):
        """Enables batch[index] list indexing"""
        return self.documents[index]
        
    def __contains__(self, filename: str) -> bool:
        """Enables 'filename in batch' membership check"""
        return any(doc.filename == filename for doc in self.documents)

doc1 = TextDocument("doc1.txt", "Text processing intro")
doc2 = TextDocument("doc2.txt", "Advanced NLP models")
batch = TextBatch([doc1, doc2])

print(len(batch))             # 2 (Calls batch.__len__())
print(batch[0].filename)      # doc1.txt (Calls batch.__getitem__(0))
print("doc2.txt" in batch)    # True (Calls batch.__contains__("doc2.txt"))
```

---

### 2.3 Comparison Protocols (`__eq__`, `__lt__`)

Implement `__eq__` for value equality comparisons (`==`) and `__lt__` for sorting (`<`).

```python
class ProcessedDocument:
    def __init__(self, filename: str, word_count: int):
        self.filename = filename
        self.word_count = word_count
        
    def __eq__(self, other) -> bool:
        """Enables doc1 == doc2 value comparison"""
        if not isinstance(other, ProcessedDocument):
            return NotImplemented
        return self.filename == other.filename and self.word_count == other.word_count

    def __lt__(self, other) -> bool:
        """Enables sorting documents by word count"""
        if not isinstance(other, ProcessedDocument):
            return NotImplemented
        return self.word_count < other.word_count

d1 = ProcessedDocument("a.txt", 100)
d2 = ProcessedDocument("b.txt", 250)
d3 = ProcessedDocument("a.txt", 100)

print(d1 == d3)        # True (Same filename & word count)
print(d1 < d2)         # True (100 < 250)

# Sorting a list of objects automatically uses __lt__!
sorted_docs = sorted([d2, d1])
print([doc.filename for doc in sorted_docs])  # ['a.txt', 'b.txt']
```

---

### 2.4 Callable Objects (`__call__`)

Implementing `__call__` allows an instance of your class to be executed like a function!

```python
class LowercaseCleaner:
    def __call__(self, text: str) -> str:
        """Enables cleaner(text) call syntax"""
        return text.lower().strip()

cleaner = LowercaseCleaner()
raw = "  NATURAL LANGUAGE PROCESSING  "

clean_text = cleaner(raw)  # 👈 Invokes cleaner.__call__(raw)
print(clean_text)          # "natural language processing"
```

---

## 3. Getters and Setters: Why & When to Use Them

### 3.1 The Problem with Direct Attribute Access

If attributes are left completely public and unmonitored, external code can assign invalid or corrupt data state:

```python
class TextDocument:
    def __init__(self, filename: str, content: str):
        self.filename = filename
        self.content = content

doc = TextDocument("sample.txt", "Valid text")

# ❌ DANGEROUS: Unvalidated direct mutation
doc.filename = ""        # Empty filename!
doc.content = None       # Crashes downstream text tokenization!
```

---

### 3.2 The Traditional (Non-Pythonic) Getter/Setter Trap

In languages like Java or C++, developers write explicit verbose methods:

```python
# ❌ Non-Pythonic Java-style (Clunky & Verbose)
class TextDocument:
    def get_content(self):
        return self._content
        
    def set_content(self, value):
        if not value:
            raise ValueError("Content cannot be empty")
        self._content = value
```
Callers are forced to type `doc.set_content("Hello")` and `doc.get_content()` everywhere.

---

### 3.3 The Pythonic Solution: `@property` Decorator

Python provides the `@property` decorator to combine **clean attribute syntax** (`doc.content`) with **active validation** behind the scenes.

```python
class TextDocument:
    def __init__(self, filename: str, content: str):
        self.filename = filename
        self.content = content  # Automatically triggers @content.setter!

    @property
    def content(self) -> str:
        """GETTER: Intercepts read access"""
        return self._content

    @content.setter
    def content(self, value: str):
        """SETTER: Intercepts write access and validates data"""
        if not isinstance(value, str):
            raise TypeError("Content must be a string!")
        if not value.strip():
            raise ValueError("Content cannot be empty or whitespace!")
        self._content = value

# Usage: Clean attribute syntax, but fully protected!
doc = TextDocument("sample.txt", "Initial text content")

doc.content = "Clean updated text"  # ✅ Passes validation
# doc.content = ""                  # 🛑 Raises ValueError: Content cannot be empty!
```

---

### 3.4 Computed & Read-Only Attributes

#### 1. Computed Attributes
Compute values dynamically on access without storing duplicate or stale data in memory:

```python
class TextDocument:
    def __init__(self, filename: str, content: str):
        self.filename = filename
        self.content = content

    @property
    def word_count(self) -> int:
        """COMPUTED PROPERTY: Calculated on-the-fly whenever accessed"""
        return len(self.content.split())

doc = TextDocument("nlp.txt", "Python text processing is fast")
print(doc.word_count)  # 5
```

#### 2. Read-Only Attributes
Omit the `.setter` to create read-only attributes that callers cannot mutate:

```python
import time

class ImmutableLogEntry:
    def __init__(self, message: str):
        self._message = message
        self._timestamp = time.strftime("%Y-%m-%d %H:%M:%S")

    @property
    def timestamp(self) -> str:
        """READ-ONLY: No setter provided"""
        return self._timestamp

log = ImmutableLogEntry("File processed successfully")
print(log.timestamp)

# log.timestamp = "2026-01-01" 
# 🛑 AttributeError: can't set attribute 'timestamp'
```

---

## 4. Summary Matrix: Dunder Methods & Properties

| Concept / Dunder | Trigger Syntax | Text Processing Example | Primary Benefit |
| :--- | :--- | :--- | :--- |
| `__init__` | `obj = Class()` | Initialize `filename` and `content` | Sets up instance attributes |
| `__str__` | `print(obj)` / `str(obj)` | `📄 Document 'sample.txt' (39 chars)` | Readable display string for users |
| `__repr__` | `repr(obj)` | `TextDocument(filename='a.txt')` | Unambiguous debug string for developers |
| `__len__` | `len(obj)` | `len(batch)` $\rightarrow$ document count | Integrates with built-in `len()` |
| `__getitem__` | `obj[index]` | `batch[0]` $\rightarrow$ first document | Enables list indexing syntax |
| `__contains__` | `item in obj` | `"doc1.txt" in batch` | Enables `in` membership testing |
| `__eq__` | `obj1 == obj2` | Compare document contents | Custom value equality logic |
| `__call__` | `obj(args)` | `cleaner("TEXT")` | Turns object instance into callable function |
| `@property` | `x = obj.attr` | `doc.word_count` (computed) | Defines getters, setters & read-only fields |
