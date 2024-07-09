# Python Async Comprehension Project

## Overview

This project explores asynchronous programming in Python by implementing asynchronous generators and comprehensions. By the end of this project, you should understand how to:

- Write an asynchronous generator.
- Use async comprehensions.
- Type-annotate asynchronous generators.

## Table of Contents

1. [Tasks](#tasks)
   - [Task 0: Async Generator](#task-0-async-generator)
   - [Task 1: Async Comprehensions](#task-1-async-comprehensions)
   - [Task 2: Run Time for Four Parallel Comprehensions](#task-2-run-time-for-four-parallel-comprehensions)
2. [Usage](#usage)
3. [Files](#files)
4. [Setup](#setup)

## Tasks

### Task 0: Async Generator

Create a coroutine called `async_generator` that:
- Loops 10 times.
- Asynchronously waits for 1 second.
- Yields a random number between 0 and 10.

**Example:**
```python
#!/usr/bin/env python3

import asyncio
import random

async def async_generator():
    for _ in range(10):
        await asyncio.sleep(1)
        yield random.uniform(0, 10)
```

### Task 1: Async Comprehensions

Create a coroutine called `async_comprehension` that:
- Collects 10 random numbers using an async comprehension over `async_generator`.
- Returns the list of 10 random numbers.

**Example:**
```python
#!/usr/bin/env python3

import asyncio

async def async_comprehension():
    return [number async for number in async_generator()]
```

### Task 2: Run Time for Four Parallel Comprehensions

Create a coroutine called `measure_runtime` that:
- Executes `async_comprehension` four times in parallel using `asyncio.gather`.
- Measures the total runtime and returns it.

**Example:**
```python
#!/usr/bin/env python3

import asyncio
import time

async def measure_runtime():
    start_time = time.time()
    await asyncio.gather(*(async_comprehension() for _ in range(4)))
    end_time = time.time()
    return end_time - start_time
```

## Usage

To use the provided functions, you can run the following scripts:

**Task 0:**
```python
#!/usr/bin/env python3

import asyncio

async_generator = __import__('0-async_generator').async_generator

async def print_yielded_values():
    result = []
    async for i in async_generator():
        result.append(i)
    print(result)

asyncio.run(print_yielded_values())
```

**Task 1:**
```python
#!/usr/bin/env python3

import asyncio

async_comprehension = __import__('1-async_comprehension').async_comprehension

async def main():
    print(await async_comprehension())

asyncio.run(main())
```

**Task 2:**
```python
#!/usr/bin/env python3

import asyncio

measure_runtime = __import__('2-measure_runtime').measure_runtime

async def main():
    print(await measure_runtime())

asyncio.run(main())
```

## Files

- `0-async_generator.py`: Contains the `async_generator` coroutine.
- `1-async_comprehension.py`: Contains the `async_comprehension` coroutine.
- `2-measure_runtime.py`: Contains the `measure_runtime` coroutine.

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/your_username/alx-backend-python.git
   cd alx-backend-python/0x02-python_async_comprehension
   ```

2. Run the example scripts:
   ```bash
   python3 0-main.py
   python3 1-main.py
   python3 2-main.py
   ```

