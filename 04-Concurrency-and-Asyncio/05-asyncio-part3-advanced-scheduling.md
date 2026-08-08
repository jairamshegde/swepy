# 🚀 Asyncio Deep Dive - Part 3: Advanced Scheduling & Safety

> **The Journey**: Breaking the rules safely by forcing non-async code into the background, and mastering mass execution with Gather vs TaskGroup.

*Based on Corey Schafer's Async.io series (Chapters 8-9).*

---

## 📑 Table of Contents
- [1. Running Blocking Code (`to_thread` / `run_in_executor`)](#1-running-blocking-code-to_thread--run_in_executor)
- [2. Gathering Results (`asyncio.gather`)](#2-gathering-results-asynciogather)
- [3. The Modern Contract (`asyncio.TaskGroup`)](#3-the-modern-contract-asynciotaskgroup)

---

## 1. Running Blocking Code (`to_thread` / `run_in_executor`)

In the previous part, we established the Cardinal Sin: You cannot run blocking, synchronous code (like `requests` or `time.sleep`) inside an asynchronous loop because it halts the entire single-thread program.

But what if you *must* use a library that hasn't been written for Asyncio yet? 

### The Solution: Offloading to Threads (For IO-Bound work)
You can command the Event Loop to spin up a background thread, throw the blocking code into that thread, and give you back an `awaitable` object.

```python
import asyncio
import requests # Synchronous, blocking library!

async def fetch_webpage(url):
    # ❌ BAD: This freezes the Event Loop completely.
    # response = requests.get(url) 
    
    # ✅ FIX: Send it to a thread! The Event loop monitors it cleanly.
    # Note: We pass the function name and arguments separated by commas.
    response = await asyncio.to_thread(requests.get, url)
    return response
```

### The Solution: Offloading to Processes (For CPU-Bound math)
If your blocking code is heavily mathematical (like image processing or Pandas calculations), a thread won't help enough because of the Python GIL (Global Interpreter Lock). You must use a Process Pool.

```python
import asyncio
from concurrent.futures import ProcessPoolExecutor

def heavy_math(number):
    return sum(i * i for i in range(number))

async def main():
    loop = asyncio.get_running_loop()
    
    # Send CPU-heavy work to an entirely isolated Process!
    result = await loop.run_in_executor(
        ProcessPoolExecutor(), 
        heavy_math, 
        10_000_000
    )
```

---

## 2. Gathering Results (`asyncio.gather`)

When you need to execute 50 tasks at once, manually writing 50 `create_task()` and `await` lines is terrible practice. 

The legacy workhorse for mass execution is `asyncio.gather`. It takes a list of coroutines, runs them all concurrently, and returns an ordered list of results.

### The "Return Exceptions" Rule
The trap of `gather` is its default error handling. If the default `return_exceptions=False` is used, and Task #42 crashes, your *entire script crashes* and you lose the results for Tasks #1-41.

**Always use `return_exceptions=True` for resilient scraping!**

```python
async def mass_download(urls):
    # Setup 100 coroutines
    tasks = [fetch_data(url) for url in urls]
    
    # *tasks unpacks the list so gather sees individual arguments.
    # return_exceptions=True means failures are returned as Exception objects, 
    # instead of violently blowing up the program.
    results = await asyncio.gather(*tasks, return_exceptions=True)
    
    for item in results:
        if isinstance(item, Exception):
            print(f"Failed Download: {item}")
        else:
            print("Successfully Downloaded!")
```

---

## 3. The Modern Contract (`asyncio.TaskGroup`)

Introduced natively in Python 3.11, the `TaskGroup` context manager is the modern, safer alternative to `gather`. 

It operates under an **All-Or-Nothing** contract. It guarantees that when you exit the block, all tasks are either fully complete, or purposefully cancelled safely.

```python
async def modern_download(urls):
    results = []
    
    # 1. Open the Context Manager
    async with asyncio.TaskGroup() as tg:
        for url in urls:
            # 2. Add tasks to the group
            task = tg.create_task(fetch_data(url))
            results.append(task)
            
    # 3. NO AWAIT NEEDED! 
    # Exiting the 'with' block automatically awaits every task inside it.
    
    # Process results after the block finishes
    for task in results:
        print(task.result())
```

### Why use TaskGroup? Fast-Failing.
If Task #5 crashes with a 404 error, the `TaskGroup` instantly triggers a massive self-destruct sequence. It actively hunts down Tasks 1-4 and 6-100 and sends cancellation signals to safely abort them. 

- Unlike `gather(return_exceptions=True)` which keeps blindly running the remaining tasks.
- If you want aggressive cancellation to save server costs, use `TaskGroup`.
- If you're building a massive web scraper where a few 404s are totally acceptable, stick to `asyncio.gather(return_exceptions=True)`.

> **Up Next**: In Part 4, we scale up to reality. Profiling bottlenecks with Scalene, dropping `requests` for native Async libraries, and avoiding IP bans with Semaphores.
