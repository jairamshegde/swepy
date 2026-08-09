# AB-200 Quick Review — Flashcards (Q1–30)

> Format matches [refresh-this.md](../refresh-this.md): read the prompt, say your answer out loud (approach + code + the one trap that matters), *then* reveal. Don't peek first — recognizing an answer isn't the same skill as producing one.
>
> This is the condensed version. For the full walkthrough — pseudocode, brute force, why the optimal version is optimal, and *all* the traps — see [Q-1-10-solutions.ipynb](Q-1-10-solutions.ipynb), [Q-11-20-solutions.ipynb](Q-11-20-solutions.ipynb), [Q-21-30-solutions.ipynb](Q-21-30-solutions.ipynb).

---

## Block 1 — Q1–10

---

**Q1. Swap Variables Without Temp**
Swap `x` and `y` without introducing a third variable.

<details>
<summary>▶ Answer</summary>

```python
x, y = y, x
```
**O(1).** The right-hand side is fully evaluated before either assignment happens — that's the "read both, then write both" trick.

**Trap:** The arithmetic version (`x=x+y; y=x-y; x=x-y`) only works on numbers and is harder to read — don't offer it as the *better* answer, just know it exists.
</details>

---

**Q2. Reverse a String**
Reverse a string.

<details>
<summary>▶ Answer</summary>

```python
s[::-1]
```
**O(n) time, O(n) space.** (`reversed(s)` + `"".join()` if you only need to *scan* backwards, O(1) extra space until materialized.)

**Trap:** Building the result with `+=` in a loop is O(n²) — strings are immutable, every concat copies. If asked to avoid slicing: two-pointer swap on `list(s)`, then `"".join()`.
</details>

---

**Q3. Palindrome Check**
Check if a string reads the same forwards and backwards (case-sensitive, spaces kept).

<details>
<summary>▶ Answer</summary>

```python
left, right = 0, len(s) - 1
while left < right:
    if s[left] != s[right]: return False
    left += 1; right -= 1
return True
```
**O(n) time, O(1) space**, with early exit on mismatch.

**Trap:** `s == s[::-1]` is a fine simple answer but is O(n) *space* and can't stop early. State your case/space convention before coding — the question is deliberately ambiguous.
</details>

---

**Q4. Factorial Calculation**
Compute n! for a non-negative integer.

<details>
<summary>▶ Answer</summary>

```python
product = 1
for i in range(2, n + 1): product *= i
```
**O(n) time, O(1) space.** (`math.factorial(n)` in real code.)

**Trap:** `0! == 1`, not undefined. Negative `n` needs an explicit reject. Naive recursion hits `RecursionError` for large `n` — Python ints don't overflow, but the call stack still has a limit.
</details>

---

**Q5. Fibonacci Sequence**
Generate the first n Fibonacci numbers (Fib(0)=0, Fib(1)=1).

<details>
<summary>▶ Answer</summary>

```python
prev, curr = 0, 1
seq = []
for _ in range(n):
    seq.append(prev)
    prev, curr = curr, prev + curr
```
**O(n) time, O(1) space.**

**Trap:** Naive recursion (`fib(k-1)+fib(k-2)`) is **O(2ⁿ)** — it recomputes the same subproblems exponentially. If you write it, immediately flag that and pivot to iteration or `@lru_cache`. Also: confirm 0-indexed vs 1-indexed convention.
</details>

---

**Q6. Prime Number Test**
Determine if n is prime.

<details>
<summary>▶ Answer</summary>

```python
if n < 2: return False
if n == 2: return True
if n % 2 == 0: return False
for i in range(3, math.isqrt(n) + 1, 2):
    if n % i == 0: return False
return True
```
**O(√n).** Divisors pair up to multiply to `n`, so one of any pair is always ≤ √n.

**Trap:** `1` is **not** prime. The √n boundary must be *inclusive* (`+1`) or perfect squares like 9 get misclassified.
</details>

---

**Q7. List Primes up to N**
List all primes ≤ N.

<details>
<summary>▶ Answer</summary>

```python
is_candidate = [True] * (N + 1)
is_candidate[0] = is_candidate[1] = False
for p in range(2, math.isqrt(N) + 1):
    if is_candidate[p]:
        for m in range(p*p, N + 1, p): is_candidate[m] = False
```
**O(N log log N).** Sieve of Eratosthenes — cross out composites in bulk instead of testing each number alone.

**Trap:** "Up to N" is inclusive (`N + 1` in both the array size and the range). Start crossing out at `p*p`, not `2*p` — smaller multiples are already handled by smaller primes.
</details>

---

**Q8. Greatest Common Divisor**
Find the GCD of two positive integers.

<details>
<summary>▶ Answer</summary>

```python
while b:
    a, b = b, a % b
return a
```
**O(log(min(a, b))).** Euclid's algorithm — `gcd(a,b) == gcd(b, a % b)`.

**Trap:** `gcd(0, n) == n` (falls out for free from the loop above). `gcd(0, 0)` is mathematically undefined; `math.gcd(0,0)` returns `0` by convention. Checking only "does the bigger one divide the smaller" is *not* the general algorithm.
</details>

---

**Q9. Count Vowels**
Count the vowels in a string.

<details>
<summary>▶ Answer</summary>

```python
sum(1 for c in s.lower() if c in frozenset('aeiou'))
```
**O(n).** No complexity win over brute force here — the real lesson is `set` membership (O(1)) vs `list` membership (O(k)).

**Trap:** Case sensitivity — lowercase first, or uppercase vowels silently don't count. `'y'` is not a vowel unless told otherwise.
</details>

---

**Q10. Word Frequency**
Count occurrences of each word in a sentence.

<details>
<summary>▶ Answer</summary>

```python
from collections import Counter
Counter(sentence.split())
```
**O(n).**

**Trap:** `.split()` (no arg) collapses whitespace runs and trims ends; `.split(" ")` doesn't — double spaces produce empty-string "words". Case and punctuation normalization are judgment calls — state which you're doing.
</details>

---

## Block 2 — Q11–20

---

**Q11. Remove Vowels from String**
Remove all vowels from a string.

<details>
<summary>▶ Answer</summary>

```python
"".join(c for c in s if c not in VOWELS_BOTH_CASE)
```
**O(n).**

**Trap:** Same `+=`-in-a-loop O(n²) trap as Q2. Handle both cases (`aeiouAEIOU`).
</details>

---

**Q12. Remove Duplicates from List**
Remove duplicates from a list, preserving order.

<details>
<summary>▶ Answer</summary>

```python
list(dict.fromkeys(items))
```
**O(n)** — relies on dicts preserving insertion order (3.7+) and deduping keys automatically.

**Trap:** `list(set(items))` removes duplicates but **does not preserve order** — fails the spec even though it "looks" right. Unhashable elements (e.g. nested lists) can't go in a `set` at all.
</details>

---

**Q13. Second Largest Number**
Find the second-largest **distinct** value in a list.

<details>
<summary>▶ Answer</summary>

```python
largest = second = float("-inf")
for n in numbers:
    if n > largest: largest, second = n, largest
    elif second < n < largest: second = n
```
**O(n) time, O(1) space.**

**Trap:** Clarify "second largest" up front — distinct value (`[5,5,3]` → `3`) vs. second position (`[5,5,3]` → `5`) are both defensible readings. Initializing trackers to `0` breaks on all-negative lists — use `-inf`.
</details>

---

**Q14. Merge Sorted Lists**
Merge two sorted lists into one sorted list.

<details>
<summary>▶ Answer</summary>

```python
i = j = 0; result = []
while i < len(a) and j < len(b):
    if a[i] <= b[j]: result.append(a[i]); i += 1
    else: result.append(b[j]); j += 1
result.extend(a[i:]); result.extend(b[j:])
```
**O(n + m).**

**Trap:** Forgetting the leftover-tail `.extend()` calls silently drops the rest of the longer list. `sorted(a + b)` "works" but throws away the fact both inputs were pre-sorted — O((n+m) log(n+m)) instead.
</details>

---

**Q15. Anagram Check**
Check if two strings are anagrams.

<details>
<summary>▶ Answer</summary>

```python
len(s1) == len(s2) and Counter(s1) == Counter(s2)
```
**O(n).**

**Trap:** `set(s1) == set(s2)` ignores frequency — fails on `"aab"` vs `"abb"` (same letters, different counts, not an anagram). Case/space handling is a judgment call, same as Q3/Q9.
</details>

---

**Q16. Sort by Second Element**
Sort a list of tuples by their second element.

<details>
<summary>▶ Answer</summary>

```python
sorted(pairs, key=lambda pair: pair[1])
```
**O(n log n), stable** (Timsort — ties keep original relative order).

**Trap:** `sorted()` returns a new list; `list.sort()` mutates in place and returns `None`. Python 3 has no `cmp=` parameter, only `key=`. Descending is `reverse=True`, not a negated key.
</details>

---

**Q17. Sum of Digits**
Sum the digits of an integer.

<details>
<summary>▶ Answer</summary>

```python
n = abs(n); total = 0
while n > 0:
    total += n % 10
    n //= 10
```
**O(d)** for a d-digit number.

**Trap:** Python's `%` on a negative number does **not** give sign-matching digits (`-907 % 10 == 3`, not `-3`) — always `abs()` first, or the loop silently computes the wrong answer without crashing.
</details>

---

**Q18. Reverse Integer Digits**
Reverse the digits of an integer, keeping its sign.

<details>
<summary>▶ Answer</summary>

```python
sign = -1 if n < 0 else 1; n = abs(n); result = 0
while n > 0:
    result = result * 10 + n % 10
    n //= 10
return sign * result
```
**O(d).**

**Trap:** Same negative-`%` issue as Q17. Trailing zeros vanish (`120` → `21`) — that's mathematically correct, not a bug (leading zero has no value as an int).
</details>

---

**Q19. All Unique Characters**
Determine if a string has all unique characters.

<details>
<summary>▶ Answer</summary>

```python
len(set(s)) == len(s)
```
**O(n).** (Or a manual loop with a `set` + early exit, if the interviewer wants short-circuiting.)

**Trap:** The "pigeonhole" pre-check (`len(s) > 128 → False`) assumes a bounded alphabet — breaks for arbitrary Unicode input.
</details>

---

**Q20. List Intersection**
Find the common elements of two lists.

<details>
<summary>▶ Answer</summary>

```python
set(list1) & set(list2)
```
**O(n + m).** (Manual loop with a `set` lookup if you need to preserve order from one input — a `set` result has no guaranteed order.)

**Trap:** Elements must be hashable. "Intersection" is ambiguous about duplicate counts — state whether you mean distinct values or multiset intersection.
</details>

---

## Block 3 — Q21–30

---

**Q21. List Subset Check**
Check if every element of one list appears in another.

<details>
<summary>▶ Answer</summary>

```python
set(smaller) <= set(larger)
```
**O(n + m).**

**Trap:** The empty list is a subset of *everything* (vacuous truth) — but nothing except empty is a subset of empty. Direction matters: "A subset of B" ≠ "B subset of A".
</details>

---

**Q22. Sort Words by Length**
Sort a list of words shortest to longest.

<details>
<summary>▶ Answer</summary>

```python
sorted(words, key=len)
```
**O(n log n), stable.**

**Trap:** `len()` counts Unicode code points, not visual glyphs — a combining accent can make two visually-identical strings report different lengths. For a tie-break secondary key: `key=lambda w: (len(w), w)`.
</details>

---

**Q23. Sort Numeric Strings**
Sort a list of numeric strings by their numeric value.

<details>
<summary>▶ Answer</summary>

```python
sorted(strings, key=int)
```
**O(n log n).**

**Trap:** Plain `sorted(strings)` (no key) sorts **lexicographically** — `"11"` comes before `"2"`. No error, no crash — just silently the wrong order. This is the whole question.
</details>

---

**Q24. Squares of Evens**
List the squares of even numbers from 1 to N.

<details>
<summary>▶ Answer</summary>

```python
[x*x for x in range(2, N + 1, 2)]
```
**O(N)** — and it's genuinely fewer operations than filtering with `% 2 == 0` on every number, since it never asks the question for odd numbers at all.

**Trap:** "1 to N" is inclusive — needs `N + 1` in the range.
</details>

---

**Q25. Dictionary Comprehension (Invert a Dict)**
Invert a dict so values map to keys.

<details>
<summary>▶ Answer</summary>

```python
{v: k for k, v in mappings.items()}
```
**O(n).**

**Trap:** Duplicate values silently overwrite — last key processed wins, earlier ones are lost, **no error**. Values must be hashable to become keys.
</details>

---

**Q26. Longest Word in Sentence**
Find the longest word in a sentence and its length.

<details>
<summary>▶ Answer</summary>

```python
words = sentence.split()
longest = max(words, key=len)
```
**O(n).**

**Trap:** `max()` on an empty sequence raises `ValueError` — guard against an empty/whitespace-only sentence. Ties resolve to the *first* maximal item (documented `max()` behavior). Punctuation attached to a word inflates its length unless stripped.
</details>

---

**Q27. Flatten Nested List (Shallow)**
Flatten a list of lists by exactly one level.

<details>
<summary>▶ Answer</summary>

```python
[item for sublist in lists for item in sublist]
```
**O(n)** in total elements.

**Trap:** `sum(lists, [])` "looks" clean but is **O(k²)** in the number of sublists — every `+=` re-copies everything accumulated so far, same disease as string concatenation in Q2. "Shallow" means exactly one level — don't accidentally write a recursive deep-flatten.
</details>

---

**Q28. Cumulative Sum**
Produce a running-total list from a list of numbers.

<details>
<summary>▶ Answer</summary>

```python
running_total = 0; result = []
for n in numbers:
    running_total += n
    result.append(running_total)
```
**O(n).** (`itertools.accumulate(numbers)` — same idea, built in, also generalizes to running max/min via its `func` argument.)

**Trap:** `[sum(numbers[:i+1]) for i in range(len(numbers))]` looks declarative but is **O(n²)** — re-sums from scratch at every index instead of carrying the total forward.
</details>

---

**Q29. Leap Year Check**
Determine if a year is a leap year.

<details>
<summary>▶ Answer</summary>

```python
year % 4 == 0 and (year % 100 != 0 or year % 400 == 0)
```
**O(1).** (`calendar.isleap(year)` in real code.)

**Trap:** Forgetting the century exception (`year % 4 == 0` alone) is **right 96% of the time** — it only fails on century years not divisible by 400 (1900 ✗, 2000 ✓). A test suite without a century-year case won't catch this bug.
</details>

---

**Q30. Transpose Matrix**
Transpose a 2D matrix (rows become columns).

<details>
<summary>▶ Answer</summary>

```python
[list(row) for row in zip(*matrix)]
```
**O(rows × cols)** — every element moves exactly once, no faster option exists.

**Trap:** `[[0] * cols] * rows` does **not** create independent rows — it repeats *one* list object by reference; mutating one "row" mutates all of them. `zip(*matrix)` silently truncates ragged (non-rectangular) input instead of raising.
</details>

---

## Cheat Sheet — One-Liners at a Glance

| # | Question | Optimal one-liner | Complexity |
|---|---|---|---|
| 1 | Swap without temp | `x, y = y, x` | O(1) |
| 2 | Reverse a string | `s[::-1]` | O(n) |
| 3 | Palindrome check | two-pointer inward walk | O(n) / O(1) space |
| 4 | Factorial | `math.factorial(n)` | O(n) |
| 5 | Fibonacci sequence | iterative two-variable slide | O(n) |
| 6 | Prime test | trial division to `isqrt(n)` | O(√n) |
| 7 | Primes up to N | Sieve of Eratosthenes | O(N log log N) |
| 8 | GCD | `math.gcd(a, b)` / Euclid's algorithm | O(log min(a,b)) |
| 9 | Count vowels | `sum(c in VOWELS for c in s.lower())` | O(n) |
| 10 | Word frequency | `Counter(sentence.split())` | O(n) |
| 11 | Remove vowels | `"".join(c for c in s if c not in VOWELS)` | O(n) |
| 12 | Remove duplicates | `list(dict.fromkeys(items))` | O(n) |
| 13 | Second largest | one-pass largest/second tracker | O(n) |
| 14 | Merge sorted lists | two-pointer merge | O(n+m) |
| 15 | Anagram check | `Counter(s1) == Counter(s2)` | O(n) |
| 16 | Sort by 2nd element | `sorted(pairs, key=lambda p: p[1])` | O(n log n) |
| 17 | Sum of digits | mod/divide loop on `abs(n)` | O(d) |
| 18 | Reverse integer | mod/divide construction | O(d) |
| 19 | All unique chars | `len(set(s)) == len(s)` | O(n) |
| 20 | List intersection | `set(a) & set(b)` | O(n+m) |
| 21 | List subset check | `set(a) <= set(b)` | O(n+m) |
| 22 | Sort words by length | `sorted(words, key=len)` | O(n log n) |
| 23 | Sort numeric strings | `sorted(strings, key=int)` | O(n log n) |
| 24 | Squares of evens | `[x*x for x in range(2, N+1, 2)]` | O(N) |
| 25 | Invert a dict | `{v: k for k, v in d.items()}` | O(n) |
| 26 | Longest word | `max(words, key=len)` | O(n) |
| 27 | Flatten (shallow) | `[x for sub in lists for x in sub]` | O(n) |
| 28 | Cumulative sum | `itertools.accumulate(numbers)` | O(n) |
| 29 | Leap year | `calendar.isleap(year)` | O(1) |
| 30 | Transpose matrix | `[list(r) for r in zip(*matrix)]` | O(rows·cols) |

**The five traps that show up more than once across this set:**
1. **Mutable-default / repeated-copy traps** — string `+=` in a loop (Q2, Q11), `sum(lists, [])` (Q27), `sum(nums[:i+1])` (Q28) — all quietly quadratic despite looking clean.
2. **Hashability requirement** — every `set()`-based upgrade (Q12, Q19, Q20, Q21, Q25) needs hashable elements or it doesn't apply at all.
3. **Case/space ambiguity, unstated** — Q3, Q9, Q10, Q11, Q15, Q19 all hinge on a convention the prompt doesn't specify. State yours before coding.
4. **Order not guaranteed from a `set`** — `list(set(x))` (Q12), `set(a) & set(b)` (Q20) both lose input order; only reach for these when order doesn't matter.
5. **Off-by-one on "inclusive" ranges** — Q6 (√n boundary), Q7 ("up to N"), Q24 ("1 to N") all need the `+ 1`.
