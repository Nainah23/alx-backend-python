
1. **Task 0: The basics of async**
   - Implement an asynchronous coroutine `wait_random` that accepts an optional `max_delay` parameter and waits for a random period (between 0 and `max_delay` seconds) before returning the delay.

2. **Task 1: Let's execute multiple coroutines at the same time with async**
   - Define an async function `wait_n` that takes two integer arguments (`n` and `max_delay`). Inside `wait_n`, spawn `n` instances of the `wait_random` coroutine with the specified `max_delay`. Collect and return the resulting delays in ascending order without using `sort()` due to concurrency.

3. **Task 2: Measure the runtime**
   - Create a function `measure_time` that measures the average execution time of `wait_n` over `n` runs. It should return the average time taken per run.

4. **Task 3: Tasks**
   - Implement a function `task_wait_random` that returns an asyncio `Task` object for the `wait_random` coroutine. This allows scheduling `wait_random` to run asynchronously.

5. **Task 4: Tasks**
   - Modify the `wait_n` function into `task_wait_n` to use `task_wait_random` for spawning asyncio tasks instead of directly calling `wait_random`. This adaptation enables concurrent execution of multiple `wait_random` tasks.

