# Introduction to Object-Oriented Programming (OOP)

This guide demonstrates the transition from a **Procedural Approach** to an **Object-Oriented Approach (OOP)** using a real-world Natural Language Processing (NLP) text processing pipeline.

---

## 📌 Sequence Navigation

This guide is part of the **Python Object-Oriented Programming (OOP) Series**:

1. **01-oops-part-1-introduction.md** 👈 *(Current Document)* — Procedural vs. OOP Intro
2. [02-oops-four-pillars.md](./02-oops-four-pillars.md) — The Four Pillars of OOP
3. [03-oops-part-2-zero2hero.md](./03-oops-part-2-zero2hero.md) — OOP Foundations, Methods & Inheritance
4. [04-dunder-methods-getters-setters.md](./04-dunder-methods-getters-setters.md) — Dunder Methods & Getters/Setters
5. [05-oops-part-3-zero2hero.md](./05-oops-part-3-zero2hero.md) — Advanced OOP (Composition, Context Managers, Generators)
6. [06-dataclasses-intuitive-guide.md](./06-dataclasses-intuitive-guide.md) — Dataclasses & Boilerplate Elimination
7. [07-design-patterns-notes.md](./07-design-patterns-notes.md) — Design Patterns in Python
8. [08-ports-and-adapters-architecture.md](./08-ports-and-adapters-architecture.md) — Ports & Adapters Architecture in Python

---

## Table of Contents
- [1. Introduction](#1-introduction)
- [2. Procedural Approach (Before OOP)](#2-procedural-approach-before-oop)
  - [2.1 Required Libraries](#21-required-libraries)
  - [2.2 Stage 1: Reading File (`read_file`)](#22-stage-1-reading-file-read_file)
  - [2.3 Stage 2: Data Quality Verification (`quality_check`)](#23-stage-2-data-quality-verification-quality_check)
  - [2.4 Stage 3: Text Preprocessing & Tokenization (`process_text`)](#24-stage-3-text-preprocessing--tokenization-process_text)
  - [2.5 Stage 4: Output & CSV Export (`save_to_csv`)](#25-stage-4-output--csv-export-save_to_csv)
  - [2.6 Procedural Pipeline Execution](#26-procedural-pipeline-execution)
  - [2.7 Drawbacks of the Procedural Approach](#27-drawbacks-of-the-procedural-approach)
- [3. Object-Oriented Approach (After OOP)](#3-object-oriented-approach-after-oop)
  - [3.1 Designing the `TextProcessor` Class](#31-designing-the-textprocessor-class)
  - [3.2 Stage 1: Running the Complete OOP Pipeline](#32-stage-1-running-the-complete-oop-pipeline)
  - [3.3 Stage 2: Extracting Insights (`get_top_words`)](#33-stage-2-extracting-insights-get_top_words)
  - [3.4 Stage 3: Internal State Inspection & Debugging](#34-stage-3-internal-state-inspection--debugging)
  - [3.5 Stage 4: Independent Step Re-execution](#35-stage-4-independent-step-re-execution)
  - [3.6 Stage 5: Inspecting Raw & Processed Attributes](#36-stage-5-inspecting-raw--processed-attributes)
- [4. Summary & Comparison](#4-summary--comparison)

---

## 1. Introduction

In traditional **Procedural Programming**, code is organized into standalone functions that operate on external data passed into them. As data pipelines grow, managing global variables, intermediate state, and function dependencies manually becomes complex and error-prone.

**Object-Oriented Programming (OOP)** solves this by bundling data (attributes) and methods (functions) into cohesive objects, maintaining internal state across pipeline stages cleanly.

---

## 2. Procedural Approach (Before OOP)

In the procedural model, each task is performed by an isolated function. Data must be explicitly passed from one function output to the next.

### 2.1 Required Libraries
Import the necessary libraries for text handling, tokenization, stop-word removal, regular expressions, and data manipulation.

```python
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
import pandas as pd
import string
import re
```

**Explanation:**
- `nltk`: Natural Language Toolkit for NLP utilities (tokenization, stop words).
- `pandas`: Used for tabular data manipulation and saving output to CSV files.
- `string` & `re`: Utilities for string translation and regex-based text processing.

---

### 2.2 Stage 1: Reading File (`read_file`)
Open a target text file and load its contents into memory as a string.

```python
# Step 1: Read file
def read_file(filename):
    with open(filename, 'r', encoding='utf-8') as file:
        return file.read()
```

**Explanation:**
- Opens the specified file safely using a context manager (`with open(...)`).
- Reads and returns the raw string content.
- **Procedural Limitation:** The returned string must be stored in a separate variable by the caller.

---

### 2.3 Stage 2: Data Quality Verification (`quality_check`)
Validate raw input text to prevent processing malformed or empty documents.

```python
def quality_check(text):
    # Check if empty
    if not text.strip():
        raise ValueError("File is empty")
    
    # Check minimum word count
    words = text.split()
    if len(words) < 2:
        raise ValueError("Text has less than 2 words")
    
    # More lenient check - just make sure it's mostly text
    # Allow letters, numbers, spaces, and common punctuation
    suspicious_chars = len([c for c in text if not (c.isalnum() or c.isspace() or c in '.,!?;:()-"\'[]{}/@#$%^&*+=<>~`')])
    if suspicious_chars > len(text) * 0.1:  # If more than 10% weird characters
        raise ValueError("Text contains too many non-standard characters")
    
    return text
```

**Explanation:**
- Ensures the text is not whitespace-only.
- Verifies a minimum threshold of words exists.
- Calculates the percentage of non-standard or corrupt characters (>10% triggers an error).
- Returns the validated text if clean, or raises a `ValueError`.

---

### 2.4 Stage 3: Text Preprocessing & Tokenization (`process_text`)
Clean the raw text, remove noise, and calculate word frequencies.

```python
# Step 3: Process text
def process_text(text):
    # Remove punctuation
    text = text.translate(str.maketrans('', '', string.punctuation))
    
    # Tokenize
    tokens = word_tokenize(text.lower())
    
    # Remove stopwords
    stop_words = set(stopwords.words('english'))
    filtered_tokens = [word for word in tokens if word not in stop_words]
    
    # Count frequency
    word_freq = {}
    for word in filtered_tokens:
        word_freq[word] = word_freq.get(word, 0) + 1
    
    return word_freq
```

**Explanation:**
- Strip out punctuation using `str.translate()`.
- Convert text to lowercase and tokenize into individual words via NLTK `word_tokenize()`.
- Filter out English stop words (e.g., "is", "the", "and").
- Build a dictionary mapping each unique word to its occurrences.

---

### 2.5 Stage 4: Output & CSV Export (`save_to_csv`)
Convert the frequency dictionary to a structured DataFrame and write it to a CSV file.

```python
# Step 4: Save to CSV
def save_to_csv(word_freq, output_file):
    df = pd.DataFrame(list(word_freq.items()), columns=['Word', 'Frequency'])
    df.to_csv(output_file, index=False)
    return output_file
```

**Explanation:**
- Converts the key-value dictionary into a Pandas DataFrame with two columns: `Word` and `Frequency`.
- Exports the DataFrame to the target CSV file without including DataFrame indices.

---

### 2.6 Procedural Pipeline Execution
Chain all individual procedural functions manually to execute the end-to-end workflow.

```python
# Your typical usage:
raw_text = read_file('input.txt')
checked_text = quality_check(raw_text)
word_frequencies = process_text(checked_text)
result_file = save_to_csv(word_frequencies, 'output.csv')
```

**Explanation:**
The developer is responsible for manually passing `raw_text` into `quality_check`, passing `checked_text` into `process_text`, and passing `word_frequencies` into `save_to_csv`.

---

### 2.7 Drawbacks of the Procedural Approach

1. **Manual Data Passing:** Every stage requires manually passing parameters and storing temporary intermediate variables (`raw_text`, `checked_text`, `word_frequencies`).
2. **Fragile Error Recovery:** If any validation step fails, intermediate state is lost, requiring a full script restart.
3. **Tight Coupling & Polluted Scope:** Global scope gets cluttered with multiple single-use variables.
4. **Difficult Debugging:** Re-running a single step (e.g., changing stop words) requires manually re-feeding input data from earlier steps.

---

## 3. Object-Oriented Approach (After OOP)

By encapsulating the entire text processing workflow inside a class (`TextProcessor`), we combine data state (raw text, word counts, output paths) and logic methods into a single self-contained object.

---

### 3.1 Designing the `TextProcessor` Class

```python
class TextProcessor:
    def __init__(self):
        self.raw_text = None
        self.checked_text = None
        self.word_frequencies = None
        self.output_file = None
    
    def read_file(self, filename):
        with open(filename, 'r', encoding='utf-8') as file:
            self.raw_text = file.read()
        print(f"✓ Read file: {len(self.raw_text)} characters")
    
    def quality_check(self):
        # Check if empty
        if not self.raw_text.strip():
            raise ValueError("File is empty")
        
        # Check minimum word count
        words = self.raw_text.split()
        if len(words) < 2:
            raise ValueError("Text has less than 2 words")
        
        # More lenient check for non-English characters
        suspicious_chars = len([c for c in self.raw_text if not (c.isalnum() or c.isspace() or c in '.,!?;:()-"\'[]{}/@#$%^&*+=<>~`')])
        if suspicious_chars > len(self.raw_text) * 0.1:
            raise ValueError("Text contains too many non-standard characters")
        
        self.checked_text = self.raw_text
        print(f"✓ Quality check passed: {len(words)} words")
    
    def process_text(self):
        # Remove punctuation
        text = self.checked_text.translate(str.maketrans('', '', string.punctuation))
        
        # Tokenize
        tokens = word_tokenize(text.lower())
        
        # Remove stopwords
        stop_words = set(stopwords.words('english'))
        filtered_tokens = [word for word in tokens if word not in stop_words]
        
        # Count frequency
        word_freq = {}
        for word in filtered_tokens:
            word_freq[word] = word_freq.get(word, 0) + 1
        
        self.word_frequencies = word_freq
        print(f"✓ Processing complete: {len(filtered_tokens)} words processed, {len(word_freq)} unique words")
    
    def save_to_csv(self, output_file):
        df = pd.DataFrame(list(self.word_frequencies.items()), columns=['Word', 'Frequency'])
        df = df.sort_values('Frequency', ascending=False)  # Sort by frequency
        df.to_csv(output_file, index=False)
        self.output_file = output_file
        print(f"✓ Saved to {output_file}")
    
    def run_pipeline(self, input_file, output_file):
        """Run the complete pipeline"""
        self.read_file(input_file)
        self.quality_check()
        self.process_text()
        self.save_to_csv(output_file)
        print("🎉 Pipeline complete!")
    
    def get_top_words(self, n=10):
        """Get top N most frequent words"""
        if self.word_frequencies:
            sorted_words = sorted(self.word_frequencies.items(), key=lambda x: x[1], reverse=True)
            return sorted_words[:n]
        return None
```

**Explanation of Methods:**
- `__init__(self)`: Initializes the object instance state variables (`self.raw_text`, `self.checked_text`, `self.word_frequencies`, `self.output_file`).
- `read_file(self, filename)`: Reads file contents directly into instance variable `self.raw_text`.
- `quality_check(self)`: Validates `self.raw_text` and assigns it to `self.checked_text`.
- `process_text(self)`: Tokenizes `self.checked_text`, removes punctuation & stop words, and stores frequency dict in `self.word_frequencies`.
- `save_to_csv(self, output_file)`: Sorts word frequencies descendingly and exports to CSV.
- `run_pipeline(self, input_file, output_file)`: Master orchestrator method that runs all steps sequentially.
- `get_top_words(self, n=10)`: Helper method leveraging stored instance state to query top $N$ frequent words.

---

### 3.2 Stage 1: Running the Complete OOP Pipeline
Instantiate a `TextProcessor` object and execute the entire pipeline with a single method call.

```python
# Complete pipeline
processor = TextProcessor()
processor.run_pipeline('input.txt', 'oops_output.csv')
```

**Output:**
```text
✓ Read file: 1068 characters
✓ Quality check passed: 141 words
✓ Processing complete: 110 words processed, 88 unique words
✓ Saved to oops_output.csv
🎉 Pipeline complete!
```

**Explanation:**
The caller simply initializes the object and calls `run_pipeline()`. All intermediate values are managed internally by the object's instance state (`self`).

---

### 3.3 Stage 2: Extracting Insights (`get_top_words`)
Query the top $N$ most frequent words directly from the instance state without re-running tokenization.

```python
# Show top words
print("\nTop 10 words:")
for word, freq in processor.get_top_words():
    print(f"{word}: {freq}")
```

**Output:**
```text
Top 10 words:
text: 8
data: 5
processing: 4
natural: 2
language: 2
machine: 2
learning: 2
analyze: 2
preprocessing: 2
analysis: 2
```

**Explanation:**
Because `self.word_frequencies` is stored inside the `processor` instance, `get_top_words()` can extract top entries instantly.

---

### 3.4 Stage 3: Internal State Inspection & Debugging
Inspect object properties at any point during or after execution.

```python
# Debugging examples:
print(f"\nFor debugging - you can inspect:")
print(f"Raw text length: {len(processor.raw_text)}")
print(f"Total unique words: {len(processor.word_frequencies)}")
```

**Output:**
```text
For debugging - you can inspect:
Raw text length: 1068
Total unique words: 88
```

**Explanation:**
Instance variables are accessible via `processor.attribute_name`, making state verification and debugging straightforward.

---

### 3.5 Stage 4: Independent Step Re-execution
Re-execute individual steps on the existing object instance without re-reading or re-validating data from scratch.

```python
# If you want to re-run just processing with different settings:
# processor.process_text()  # Just this step
# processor.save_to_csv('output2.csv')  # Just this step
```

**Explanation:**
Because raw and checked text remain saved inside `processor.checked_text`, individual methods like `process_text()` or `save_to_csv()` can be invoked independently.

---

### 3.6 Stage 5: Inspecting Raw & Processed Attributes

```python
processor.word_frequencies
```

```python
print(processor.raw_text)
```

**Output:**
```text
Natural language processing is a fascinating field that combines computer science and linguistics. Machine learning algorithms can analyze text data to extract meaningful insights and patterns. Text preprocessing is crucial for effective natural language processing tasks.

Python provides excellent libraries like NLTK and spaCy for text analysis. These tools help developers clean, tokenize, and analyze textual data efficiently. Regular expressions are also valuable for pattern matching in text processing applications.

Data scientists often work with large datasets containing unstructured text. Cleaning and preprocessing this data requires careful attention to encoding issues, special characters, and language-specific considerations. The quality of input data directly impacts the performance of machine learning models.

Text mining techniques enable organizations to discover valuable information from documents, emails, social media posts, and other text sources. Word frequency analysis is one fundamental approach used in many text processing pipelines.
```

**Explanation:**
Viewing `processor.word_frequencies` and `processor.raw_text` demonstrates encapsulation — data remains persistently stored inside the object and accessible whenever needed.

---

## 4. Summary & Comparison

| Feature / Aspect | Procedural Approach (Before OOP) | Object-Oriented Approach (After OOP) |
| :--- | :--- | :--- |
| **State Management** | Manual via multiple isolated variables | Automatic via instance attributes (`self`) |
| **Data Flow** | Arguments explicitly passed between functions | Encapsulated inside object instance |
| **Reusability** | Low (script-bound function chains) | High (instantiable, reusable classes) |
| **Debugging** | Difficult (loss of context across steps) | Easy (inspect attributes on object at any time) |
| **Modularity & Scalability** | Prone to scope pollution and breaking changes | Clean encapsulation and easy to extend via inheritance/polymorphism |
