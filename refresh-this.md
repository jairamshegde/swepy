# Python Fundamentals

> Format: every problem is written the way an interviewer asks it. No preamble. Just the prompt, expected output, and the answer you need to give — clean and fast.


## Block 1 — Output Prediction (What Does This Print?)

> Warm-up category. Interviewers throw these in the first 5 minutes. Get them cold.

---

**Q1.**
```python
x = [1, 2, 3]
y = x
y.append(4)
print(x)
```

<details>
<summary>▶ Answer</summary>

**`[1, 2, 3, 4]`**

`y = x` is not a copy — both names point to the same list object. To copy: `y = x[:]` or `y = x.copy()`.

</details>

---

**Q2.**
```python
a = (1, [2, 3], 4)
a[1].append(5)
print(a)
```

<details>
<summary>▶ Answer</summary>

**`(1, [2, 3, 5], 4)`**

The tuple is immutable but the list *inside* it is mutable. Tuple immutability means you can't reassign `a[1]`, but you can mutate what it points to.

</details>

---

**Q3.**
```python
def f(x, data=[]):
    data.append(x)
    return data

print(f(1))
print(f(2))
print(f(3, []))
print(f(4))
```

<details>
<summary>▶ Answer</summary>

**`[1]` → `[1, 2]` → `[3]` → `[1, 2, 4]`**

Default list is created once at function definition and shared across calls. `f(3, [])` passes a fresh list so it doesn't affect the default. Classic mutable default trap.

</details>

---

**Q4.**
```python
x = 5
def outer():
    x = 10
    def inner():
        print(x)
    inner()

outer()
print(x)
```

<details>
<summary>▶ Answer</summary>

**`10` then `5`**

LEGB rule — `inner()` sees `x = 10` from its enclosing scope. The global `x = 5` is untouched.

</details>

---

**Q5.**
```python
print(0.1 + 0.2 == 0.3)
print(round(0.1 + 0.2, 1) == 0.3)
```

<details>
<summary>▶ Answer</summary>

**`False` then `True`**

Floating-point representation error. Use `round()` or `math.isclose()` for float comparisons in production.

</details>

---

**Q6.**
```python
a = [1, 2, 3]
b = a[:]
b.append(4)
print(a)
print(b)
```

<details>
<summary>▶ Answer</summary>

**`[1, 2, 3]` then `[1, 2, 3, 4]`**

Slice creates a shallow copy. Appending to `b` doesn't affect `a`. But if the list contained nested objects, those would still be shared.

</details>

---

**Q7.**
```python
nums = [1, 2, 3, 4, 5]
print(nums[1:4])
print(nums[::2])
print(nums[::-1])
```

<details>
<summary>▶ Answer</summary>

**`[2, 3, 4]` → `[1, 3, 5]` → `[5, 4, 3, 2, 1]`**

Standard slicing. `[start:stop:step]`. Negative step reverses.

</details>

---

**Q8.**
```python
x = [i**2 for i in range(5) if i % 2 == 0]
print(x)
```

<details>
<summary>▶ Answer</summary>

**`[0, 4, 16]`**

List comprehension with filter. `range(5)` → 0,1,2,3,4 → even values 0,2,4 → squared.

</details>

---

**Q9.**
```python
d = {'a': 1, 'b': 2}
print(d.get('c', 0))
print(d.get('a', 99))
```

<details>
<summary>▶ Answer</summary>

**`0` then `1`**

`.get(key, default)` returns default if key missing, actual value if present.

</details>

---

**Q10.**
```python
s = {1, 2, 3}
s.add(2)
s.add(4)
print(sorted(s))
```

<details>
<summary>▶ Answer</summary>

**`[1, 2, 3, 4]`**

Sets have no duplicates. Adding `2` again is a no-op. Sets are unordered, so `sorted()` for predictable output.

</details>

---

## Block 2 — Fix the Bug

> Interviewer shows you broken code. You spot the issue and fix it in under 60 seconds.

---

**Q11. Find the bug:**
```python
# Goal: return True if all elements are positive
def all_positive(nums):
    for n in nums:
        if n > 0:
            return True
    return False

print(all_positive([1, -2, 3]))  # Should be False
```

<details>
<summary>▶ Answer</summary>

**Bug:** Returns `True` on the first positive number instead of checking all.

**Fix:**
```python
def all_positive(nums):
    for n in nums:
        if n <= 0:
            return False
    return True
# Or: return all(n > 0 for n in nums)
```

</details>

---

**Q12. Find the bug:**
```python
# Goal: remove duplicates while preserving order
def dedupe(items):
    return list(set(items))

print(dedupe([3, 1, 2, 1, 3]))  # May not preserve order
```

<details>
<summary>▶ Answer</summary>

**Bug:** `set()` doesn't preserve insertion order.

**Fix:**
```python
def dedupe(items):
    seen = set()
    return [x for x in items if not (x in seen or seen.add(x))]
# Or use dict.fromkeys() which preserves insertion order in Python 3.7+:
# return list(dict.fromkeys(items))
```

</details>

---

**Q13. Find the bug:**
```python
# Goal: safely divide, return 0 on division by zero
def safe_divide(a, b):
    try:
        return a / b
    except:
        return 0
```

<details>
<summary>▶ Answer</summary>

**Bug:** Bare `except:` catches *everything* including `KeyboardInterrupt`, `SystemExit`. Always catch specific exceptions.

**Fix:**
```python
def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return 0
```

</details>

---

**Q14. Find the bug:**
```python
# Goal: concatenate a list of strings efficiently
parts = ["Hello", " ", "World", "!"]
result = ""
for p in parts:
    result += p
print(result)
```

<details>
<summary>▶ Answer</summary>

**Bug:** String `+=` in a loop creates a new string object each iteration → O(n²) in the worst case.

**Fix:**
```python
result = "".join(parts)
```

</details>

---

**Q15. Find the bug:**
```python
# Goal: count character frequency
text = "hello"
freq = {}
for ch in text:
    freq[ch] += 1
print(freq)
```

<details>
<summary>▶ Answer</summary>

**Bug:** `KeyError` on first access — key doesn't exist yet.

**Fix (3 options):**
```python
# Option 1 — setdefault
freq.setdefault(ch, 0)
freq[ch] += 1

# Option 2 — get
freq[ch] = freq.get(ch, 0) + 1

# Option 3 — defaultdict (cleanest)
from collections import defaultdict
freq = defaultdict(int)
for ch in text:
    freq[ch] += 1
```

</details>

---

## Block 3 — Implement This (10-Minute Problems)

> Interviewer says "write this function." These should take under 10 minutes each.

---

**Q16. Flatten a nested list (arbitrary depth)**
```
Input:  [1, [2, [3, 4], 5], 6]
Output: [1, 2, 3, 4, 5, 6]
```

<details>
<summary>▶ Answer</summary>

```python
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result
```

**Follow-up:** Generator version (memory-efficient for huge nested structures):
```python
def flatten_gen(lst):
    for item in lst:
        if isinstance(item, list):
            yield from flatten_gen(item)
        else:
            yield item
```

</details>

---

**Q17. Group anagrams together**
```
Input:  ["eat", "tea", "tan", "ate", "nat", "bat"]
Output: [["eat","tea","ate"], ["tan","nat"], ["bat"]]
```

<details>
<summary>▶ Answer</summary>

```python
from collections import defaultdict

def group_anagrams(words):
    groups = defaultdict(list)
    for word in words:
        key = tuple(sorted(word))
        groups[key].append(word)
    return list(groups.values())
```

</details>

---

**Q18. Implement `zip()` from scratch**
```
zip([1,2,3], ['a','b','c']) → [(1,'a'), (2,'b'), (3,'c')]
```

<details>
<summary>▶ Answer</summary>

```python
def my_zip(*iterables):
    iters = [iter(it) for it in iterables]
    while True:
        result = []
        for it in iters:
            try:
                result.append(next(it))
            except StopIteration:
                return
        yield tuple(result)
```

</details>

---

**Q19. Implement a generator for fibonacci numbers**
```
Yields: 0, 1, 1, 2, 3, 5, 8, ...
```

<details>
<summary>▶ Answer</summary>

```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

# Usage: take first 8
gen = fibonacci()
print([next(gen) for _ in range(8)])
# [0, 1, 1, 2, 3, 5, 8, 13]
```

**Why generators matter here:** Infinite sequence. You can't store all fibonacci numbers — you yield them lazily.

</details>

---

**Q20. Implement a timing decorator**

<details>
<summary>▶ Answer</summary>

```python
import time
import functools

def timer(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        result = func(*args, **kwargs)
        elapsed = time.perf_counter() - start
        print(f"{func.__name__} took {elapsed:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(0.1)
    return "done"
```

**Key detail:** `@functools.wraps(func)` preserves the original function's `__name__` and `__doc__`. Always include it in real decorators.

</details>

---

**Q21. Implement a retry decorator**

<details>
<summary>▶ Answer</summary>

```python
import time
import functools

def retry(max_attempts=3, delay=1.0, exceptions=(Exception,)):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(1, max_attempts + 1):
                try:
                    return func(*args, **kwargs)
                except exceptions as e:
                    if attempt == max_attempts:
                        raise
                    print(f"Attempt {attempt} failed: {e}. Retrying in {delay}s...")
                    time.sleep(delay)
        return wrapper
    return decorator

@retry(max_attempts=3, delay=0.5, exceptions=(ConnectionError,))
def call_api():
    ...
```

</details>

---

**Q22. Context manager using a class** — implement one that times a code block

<details>
<summary>▶ Answer</summary>

```python
import time

class Timer:
    def __enter__(self):
        self.start = time.perf_counter()
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.elapsed = time.perf_counter() - self.start
        print(f"Elapsed: {self.elapsed:.4f}s")
        return False  # Don't suppress exceptions

with Timer() as t:
    time.sleep(0.2)
# prints: Elapsed: 0.2001s
```

**Follow-up:** Same thing using `@contextlib.contextmanager`:
```python
from contextlib import contextmanager

@contextmanager
def timer():
    start = time.perf_counter()
    yield
    print(f"Elapsed: {time.perf_counter() - start:.4f}s")
```

</details>

---

**Q23. Implement `defaultdict` behaviour from scratch**

<details>
<summary>▶ Answer</summary>

```python
class MyDefaultDict(dict):
    def __init__(self, default_factory, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.default_factory = default_factory

    def __missing__(self, key):
        if self.default_factory is None:
            raise KeyError(key)
        self[key] = self.default_factory()
        return self[key]

d = MyDefaultDict(list)
d["a"].append(1)
d["a"].append(2)
print(d)  # {'a': [1, 2]}
```

</details>

---

**Q24. Batch an iterable into chunks of size N**
```
Input:  [1,2,3,4,5,6,7], n=3
Output: [[1,2,3], [4,5,6], [7]]
```

<details>
<summary>▶ Answer</summary>

```python
def batch(iterable, n):
    lst = list(iterable)
    return [lst[i:i+n] for i in range(0, len(lst), n)]

# Generator version (memory-efficient):
def batch_gen(iterable, n):
    it = iter(iterable)
    while chunk := list(itertools.islice(it, n)):
        yield chunk
```

**AI relevance:** Exactly the pattern for batching embedding API calls.

</details>

---

**Q25. Flatten a dict to dot-notation keys**
```
Input:  {"a": {"b": {"c": 1}}, "d": 2}
Output: {"a.b.c": 1, "d": 2}
```

<details>
<summary>▶ Answer</summary>

```python
def flatten_dict(d, prefix=""):
    result = {}
    for key, value in d.items():
        full_key = f"{prefix}.{key}" if prefix else key
        if isinstance(value, dict):
            result.update(flatten_dict(value, full_key))
        else:
            result[full_key] = value
    return result
```

</details>

---

## Block 4 — Collections & Built-ins Mastery

> Interviewers check if you reach for the right tool. These are "what would you use and why" + quick implementations.

---

**Q26. When do you use `deque` over a list?**

<details>
<summary>▶ Answer</summary>

Use `deque` when you need O(1) appends and pops from *both ends*.

```python
from collections import deque

# Sliding window of last N items
window = deque(maxlen=3)
for x in [1, 2, 3, 4, 5]:
    window.append(x)
    print(list(window))
# [1] → [1,2] → [1,2,3] → [2,3,4] → [3,4,5]
```

List `pop(0)` is O(n). `deque.popleft()` is O(1). **Critical for RAG sliding-window context management.**

</details>

---

**Q27. Use `Counter` to find the most common K words**

<details>
<summary>▶ Answer</summary>

```python
from collections import Counter

text = "the cat sat on the mat the cat"
words = text.split()
freq = Counter(words)
print(freq.most_common(2))
# [('the', 3), ('cat', 2)]

# Counter arithmetic:
c1 = Counter("aab")
c2 = Counter("abb")
print(c1 + c2)  # Counter({'a': 3, 'b': 3})
print(c1 - c2)  # Counter({'a': 1})  — subtracts, drops zero/negatives
```

</details>

---

**Q28. Use `defaultdict` to build an inverted index**

<details>
<summary>▶ Answer</summary>

```python
from collections import defaultdict

docs = {
    0: "cat sat on mat",
    1: "dog sat on floor",
    2: "cat chased dog"
}

inverted = defaultdict(set)
for doc_id, text in docs.items():
    for word in text.split():
        inverted[word].add(doc_id)

print(inverted["cat"])  # {0, 2}
print(inverted["sat"])  # {0, 1}
```

**AI relevance:** An inverted index is the core data structure inside BM25 and keyword search engines.

</details>

---

**Q29. `heapq` — Top-K elements from a large stream**

<details>
<summary>▶ Answer</summary>

```python
import heapq

# Top-3 from a stream (without sorting all)
stream = [5, 1, 9, 3, 7, 2, 8]
top_k = heapq.nlargest(3, stream)
print(top_k)  # [9, 8, 7]

# Using a min-heap of fixed size K:
def top_k_stream(stream, k):
    heap = []
    for x in stream:
        heapq.heappush(heap, x)
        if len(heap) > k:
            heapq.heappop(heap)
    return sorted(heap, reverse=True)
```

**AI relevance:** Top-K retrieval in vector search. Maintaining top-K candidates without loading all results.

</details>

---

**Q30. `itertools` — Cartesian product and sliding windows**

<details>
<summary>▶ Answer</summary>

```python
import itertools

# All pairs from two lists (e.g., test all prompt × model combinations)
prompts = ["P1", "P2"]
models  = ["gpt", "claude"]
combos  = list(itertools.product(prompts, models))
# [('P1','gpt'), ('P1','claude'), ('P2','gpt'), ('P2','claude')]

# Sliding windows of size N
def windows(iterable, n):
    it = iter(iterable)
    win = tuple(itertools.islice(it, n))
    if len(win) == n:
        yield win
    for item in it:
        win = win[1:] + (item,)
        yield win

print(list(windows([1,2,3,4,5], 3)))
# [(1,2,3), (2,3,4), (3,4,5)]
```

</details>

---

**Q31. `functools.lru_cache` — When and how**

<details>
<summary>▶ Answer</summary>

```python
from functools import lru_cache

@lru_cache(maxsize=128)
def expensive_embedding(text: str) -> tuple:
    # Simulates an API call
    return tuple(hash(c) for c in text)

# LRU cache is keyed by arguments — arguments must be hashable
# Lists are not hashable → convert to tuple before passing

texts = ["hello", "world", "hello"]
for t in texts:
    print(expensive_embedding(t))  # "hello" computed once, cached on second call

print(expensive_embedding.cache_info())
# CacheInfo(hits=1, misses=2, maxsize=128, currsize=2)
```

</details>

---

## Block 5 — OOP for Interviews

> Senior roles expect clean class design. These are the patterns that come up.

---

**Q32. Implement a Singleton**

<details>
<summary>▶ Answer</summary>

```python
class Singleton:
    _instance = None

    def __new__(cls, *args, **kwargs):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

a = Singleton()
b = Singleton()
print(a is b)  # True
```

**AI use case:** Single shared LLM client, shared config object across an agent pipeline.

</details>

---

**Q33. `@property` — Validate on set**

<details>
<summary>▶ Answer</summary>

```python
class TokenBudget:
    def __init__(self, max_tokens: int):
        self.max_tokens = max_tokens  # calls setter
        self._used = 0

    @property
    def max_tokens(self):
        return self._max_tokens

    @max_tokens.setter
    def max_tokens(self, value):
        if value <= 0:
            raise ValueError("max_tokens must be positive")
        self._max_tokens = value

    @property
    def remaining(self):
        return self._max_tokens - self._used
```

</details>

---

**Q34. `__repr__` vs `__str__` — what's the difference?**

<details>
<summary>▶ Answer</summary>

```python
class Chunk:
    def __init__(self, text, score):
        self.text = text
        self.score = score

    def __str__(self):
        return f"Chunk(score={self.score:.2f})"  # for end users / print()

    def __repr__(self):
        return f"Chunk(text={self.text!r}, score={self.score})"  # for debugging / repr()

c = Chunk("hello world", 0.92)
print(str(c))   # Chunk(score=0.92)
print(repr(c))  # Chunk(text='hello world', score=0.92)
```

**Rule:** `__repr__` should produce a string that could recreate the object. `__str__` is for human display.

</details>

---

**Q35. Dataclass for clean data containers**

<details>
<summary>▶ Answer</summary>

```python
from dataclasses import dataclass, field
from typing import Optional

@dataclass
class RetrievedChunk:
    doc_id: str
    text: str
    score: float
    metadata: dict = field(default_factory=dict)
    reranked_score: Optional[float] = None

    def __post_init__(self):
        if not 0.0 <= self.score <= 1.0:
            raise ValueError(f"Score {self.score} out of [0,1] range")

c = RetrievedChunk(doc_id="d1", text="hello", score=0.85)
print(c)
# RetrievedChunk(doc_id='d1', text='hello', score=0.85, metadata={}, reranked_score=None)
```

**Why interviewers love this question:** It reveals if you know modern Python. `@dataclass` removes boilerplate `__init__`, `__repr__`, `__eq__` while adding validation via `__post_init__`.

</details>

---

## Block 6 — Async & Concurrency (Fast Reference)

> "Which model do you use and why?" — this is the question. Know the answer cold.

---

**Q36. Thread vs Process vs Asyncio — decision tree**

<details>
<summary>▶ Answer</summary>

| Task type | Use |
|---|---|
| I/O-bound (API calls, file reads, DB queries) | `asyncio` or `threading` |
| CPU-bound (heavy computation, matrix ops) | `multiprocessing` |
| Mixed I/O with existing sync library | `threading` with `ThreadPoolExecutor` |
| High-concurrency I/O (1000+ simultaneous) | `asyncio` |

**The GIL:** CPython's Global Interpreter Lock allows only one thread to execute Python bytecode at a time. Threading doesn't help for CPU-bound work — use multiprocessing.

</details>

---

**Q37. `asyncio` — basic coroutine pattern for parallel API calls**

<details>
<summary>▶ Answer</summary>

```python
import asyncio

async def fetch_embedding(text: str) -> list[float]:
    await asyncio.sleep(0.1)  # simulates API latency
    return [0.1, 0.2, 0.3]

async def process_batch(texts: list[str]) -> list[list[float]]:
    tasks = [fetch_embedding(t) for t in texts]
    return await asyncio.gather(*tasks)

results = asyncio.run(process_batch(["a", "b", "c"]))
```

**Key:** `asyncio.gather()` runs coroutines concurrently. All 3 `fetch_embedding` calls run during each other's `await asyncio.sleep`.

</details>

---

**Q38. Semaphore — cap concurrent API calls**

<details>
<summary>▶ Answer</summary>

```python
import asyncio

async def bounded_embed(sem, text):
    async with sem:
        await asyncio.sleep(0.1)  # API call
        return f"embedding({text})"

async def main():
    sem = asyncio.Semaphore(3)  # max 3 concurrent calls
    tasks = [bounded_embed(sem, f"doc{i}") for i in range(10)]
    results = await asyncio.gather(*tasks)
    return results

asyncio.run(main())
```

</details>

---

**Q39. `ThreadPoolExecutor` for sync code you can't make async**

<details>
<summary>▶ Answer</summary>

```python
from concurrent.futures import ThreadPoolExecutor, as_completed

def sync_embed(text):
    # Legacy sync SDK that can't be awaited
    import time; time.sleep(0.1)
    return f"vec({text})"

texts = [f"doc{i}" for i in range(10)]

with ThreadPoolExecutor(max_workers=5) as executor:
    futures = {executor.submit(sync_embed, t): t for t in texts}
    for future in as_completed(futures):
        text = futures[future]
        result = future.result()
        print(f"{text}: {result}")
```

</details>

---

## Block 7 — String & File Operations

> AI engineers process text constantly. These are the practical patterns.

---

**Q40. Parse structured text from LLM output**

<details>
<summary>▶ Answer</summary>

```python
import re

raw = """
Name: Jairam Hegde
Role: Lead AI Engineer
Score: 0.92
Tags: RAG, Agents, LLMs
"""

def parse_fields(text):
    result = {}
    for line in text.strip().splitlines():
        if ":" in line:
            key, _, value = line.partition(":")
            result[key.strip()] = value.strip()
    return result

print(parse_fields(raw))
# {'Name': 'Jairam Hegde', 'Role': 'Lead AI Engineer', 'Score': '0.92', 'Tags': 'RAG, Agents, LLMs'}
```

</details>

---

**Q41. Stream-read a large file without loading it all**

<details>
<summary>▶ Answer</summary>

```python
def stream_chunks(filepath, chunk_size=1024):
    """Read a large file in chunks — never loads full file into memory."""
    with open(filepath, 'r', encoding='utf-8') as f:
        while True:
            chunk = f.read(chunk_size)
            if not chunk:
                break
            yield chunk

# Line-by-line (even better for text):
def stream_lines(filepath):
    with open(filepath, 'r') as f:
        for line in f:      # file objects are their own iterators
            yield line.rstrip()
```

</details>

---

**Q42. Extract JSON from a string that has other content**

<details>
<summary>▶ Answer</summary>

```python
import json, re

def extract_json(text: str) -> dict | None:
    """Extract first valid JSON object from a mixed string."""
    match = re.search(r'\{.*\}', text, re.DOTALL)
    if match:
        try:
            return json.loads(match.group())
        except json.JSONDecodeError:
            return None
    return None

llm_output = 'Sure! Here is the result: {"name": "Jairam", "score": 0.9} Hope that helps!'
print(extract_json(llm_output))
# {'name': 'Jairam', 'score': 0.9}
```

**AI relevance:** This is the exact function you need when your LLM doesn't use structured outputs and wraps JSON in prose.

</details>

---

## Block 8 — Type Hints & Modern Python (Quick Wins)

> Companies expect type hints at Lead level. These take 10 minutes to nail.

---

**Q43. Annotate a function correctly**

<details>
<summary>▶ Answer</summary>

```python
from typing import Optional, Union

def get_embedding(
    text: str,
    model: str = "text-embedding-3-small",
    timeout: Optional[float] = None
) -> list[float]:
    ...

# Union (Python 3.9 style):
def parse_score(value: Union[str, float]) -> float:
    return float(value)

# Python 3.10+ shorthand:
def parse_score(value: str | float) -> float:
    return float(value)
```

</details>

---

**Q44. `TypedDict` for structured dicts**

<details>
<summary>▶ Answer</summary>

```python
from typing import TypedDict

class ChunkResult(TypedDict):
    doc_id: str
    text: str
    score: float
    metadata: dict

def search(query: str) -> list[ChunkResult]:
    ...
```

Use `TypedDict` when a dict has a fixed, known set of keys — cleaner than a plain dict, lighter than a dataclass.

</details>

---

**Q45. Protocol for duck-typing**

<details>
<summary>▶ Answer</summary>

```python
from typing import Protocol

class Retriever(Protocol):
    def search(self, query: str, top_k: int) -> list[dict]: ...

# Any class implementing .search() with the right signature satisfies this —
# no inheritance needed. Clean for swapping between BM25, dense, and hybrid retrievers.

class BM25Retriever:
    def search(self, query: str, top_k: int) -> list[dict]:
        ...

def run_pipeline(retriever: Retriever, query: str):
    return retriever.search(query, top_k=5)
```

</details>

---

## Block 9 — Performance & Memory

> Senior-level filter questions. Interviewers want to hear "I measured" and "I chose the right tool."

---

**Q46. List comprehension vs `map()` vs loop — when to use which?**

<details>
<summary>▶ Answer</summary>

```python
# All three do the same thing:
nums = range(1_000_000)

# List comprehension — Pythonic, fast, readable. Use by default.
squares = [x**2 for x in nums]

# map() — lazy iterator, slightly faster if you're feeding into another iterator
squares_map = map(lambda x: x**2, nums)

# Generator — best when you DON'T need all results at once
squares_gen = (x**2 for x in nums)
```

**Rule of thumb:**
- Need all results in memory → list comprehension
- Piping into another iterator → `map()` or generator
- Infinite / very large stream → generator

</details>

---

**Q47. Profile code quickly with `timeit`**

<details>
<summary>▶ Answer</summary>

```python
import timeit

# Compare string concat methods
t1 = timeit.timeit('"-".join(str(n) for n in range(100))', number=10_000)
t2 = timeit.timeit(
    stmt='result = ""; \nfor n in range(100): result += str(n) + "-"',
    number=10_000
)
print(f"join: {t1:.3f}s | concat: {t2:.3f}s")
# join is typically 2–4x faster
```

</details>

---

**Q48. Memory-efficient: `__slots__`**

<details>
<summary>▶ Answer</summary>

```python
class WithSlots:
    __slots__ = ['doc_id', 'score', 'embedding']
    def __init__(self, doc_id, score, embedding):
        self.doc_id = doc_id
        self.score = score
        self.embedding = embedding

class WithoutSlots:
    def __init__(self, doc_id, score, embedding):
        self.doc_id = doc_id
        self.score = score
        self.embedding = embedding
```

`__slots__` prevents creation of `__dict__` per instance — saves ~40–50% memory when you have millions of objects (e.g., storing 1M retrieved chunks).

</details>

---

## Block 10 — Quick-Fire (30 Seconds Each)

> Last section. These should be instant answers.

---

**Q49.** What is the difference between `is` and `==`?

<details>
<summary>▶ Answer</summary>

`==` checks value equality. `is` checks identity (same object in memory).

```python
a = [1, 2]
b = [1, 2]
a == b  # True
a is b  # False
```

</details>

---

**Q50.** What does `*args` and `**kwargs` do?

<details>
<summary>▶ Answer</summary>

`*args` collects extra positional arguments as a tuple. `**kwargs` collects extra keyword arguments as a dict. Used in wrappers and decorators to forward arguments without knowing them.

</details>

---

**Q51.** What is a closure?

<details>
<summary>▶ Answer</summary>

A function that captures variables from its enclosing scope even after that scope has exited.

```python
def make_multiplier(n):
    def multiply(x):
        return x * n   # n is captured from enclosing scope
    return multiply

double = make_multiplier(2)
print(double(5))  # 10
```

</details>

---

**Q52.** `list` vs `tuple` — when do you choose tuple?

<details>
<summary>▶ Answer</summary>

Tuple when data is fixed and should not change (coordinates, RGB values, config pairs), and for use as dict keys (tuples are hashable, lists are not).

</details>

---

**Q53.** What does `yield from` do?

<details>
<summary>▶ Answer</summary>

Delegates to a sub-generator — cleaner than looping and yielding manually.

```python
def chain(*iters):
    for it in iters:
        yield from it
print(list(chain([1,2], [3,4], [5])))  # [1, 2, 3, 4, 5]
```

</details>

---

**Q54.** How do you reverse a dict?

<details>
<summary>▶ Answer</summary>

```python
{v: k for k, v in d.items()}
```

Only works if values are unique and hashable.

</details>

---

**Q55.** What is `enumerate()` and when do you use it?

<details>
<summary>▶ Answer</summary>

Returns `(index, value)` pairs while iterating. Use whenever you need both the index and value. Never use `range(len(lst))` — use `enumerate(lst)`.

</details>

---

**Q56.** Difference between `sorted()` and `.sort()`?

<details>
<summary>▶ Answer</summary>

`sorted()` returns a new list, works on any iterable. `.sort()` sorts in-place, only on lists.

</details>

---

**Q57.** What is the GIL?

<details>
<summary>▶ Answer</summary>

Global Interpreter Lock — a mutex in CPython that allows only one thread to execute Python bytecode at a time. Threads are fine for I/O-bound work. For CPU-bound parallelism, use `multiprocessing`.

</details>

---

**Q58.** How do you merge two dicts in Python 3.9+?

<details>
<summary>▶ Answer</summary>

```python
merged = d1 | d2        # right-side values win on conflict
d1 |= d2                # in-place
```

</details>

---

**Q59.** What does `@staticmethod` vs `@classmethod` do?

<details>
<summary>▶ Answer</summary>

`@staticmethod` — no access to `self` or `cls`, just a regular function namespaced to the class.

`@classmethod` — receives `cls` as first argument; used for alternative constructors.

```python
class Config:
    @classmethod
    def from_dict(cls, d: dict):
        return cls(**d)

    @staticmethod
    def validate_key(key: str) -> bool:
        return key.isidentifier()
```

</details>

---

**Q60.** How do you make a class iterable?

<details>
<summary>▶ Answer</summary>

Implement `__iter__` (returns `self` or an iterator object) and `__next__` (returns next value, raises `StopIteration` when done).

</details>

---

## Cheat Sheet — Key Complexity

| Operation | Data Structure | Time Complexity |
|---|---|---|
| Lookup by key | `dict` | O(1) avg |
| Membership test | `set` | O(1) avg |
| Membership test | `list` | O(n) |
| Append to end | `list` | O(1) amortized |
| Insert at front | `list` | O(n) |
| Append/pop either end | `deque` | O(1) |
| Push/pop | `heapq` | O(log n) |
| Sorted insert | `bisect` | O(log n) search, O(n) insert |
| Sorting | any | O(n log n) — TimSort |
