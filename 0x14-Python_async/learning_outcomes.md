# 0x01. Python - Async

## Python

## Back-end

### Resources

Read or watch:

- [Async IO in Python: A Complete Walkthrough](https://realpython.com/async-io-python/)
- [asyncio - Asynchronous I/O](https://docs.python.org/3/library/asyncio.html)
- [random.uniform](https://docs.python.org/3/library/random.html#random.uniform)

## Definitions

### Asynchronous Programming

Asynchronous programming is a method of programming that allows for the execution of tasks in a non-blocking manner. This means that tasks can be executed in the background, and other tasks can continue to run without waiting for the previous ones to complete.

## `async` and `await` Syntax

- In Python, the `async` and `await` keywords are used to define and manage asynchronous functions
- An `async` function is a function that can be paused and resumed, allowing other functions to run in the meantime.
- The `await` keyword is used to pause the execution of an `async` function until the awaited task is complete.

## Examples of `async` and `await` Syntax

### Basic `async` and `await` Usage

The `async` keyword is used to define an asynchronous function, also known as a coroutine. The `await` keyword is used to pause the execution of the coroutine until the awaited task is complete. Here's a basic example:

    import asyncio

    async def say_hello():
        print("Hello")
        await asyncio.sleep(1)
        print("World")

    asyncio.run(say_hello())

__Explanation:__

1. `async def say_hello():` defines an asynchronous function.
   
2. `await asyncio.sleep(1)` pauses the execution of say_hello for 1 second.

3. After the pause, the function resumes and prints "World".

### Awaiting Multiple Coroutines

You can run multiple asynchronous functions concurrently and await their results.

    import asyncio

    async def greet(name):
        print(f"Hello, {name}")
        await asyncio.sleep(1)
        print(f"Goodbye, {name}")

    async def main():
        await asyncio.gather(
            greet("Alice"),
            greet("Bob"),
            greet("Charlie")
        )

    asyncio.run(main())

__Explanation:__

1. `greet(name)` is an asynchronous function that prints a greeting, waits for 1 second, and then prints a goodbye message.
   
2. `asyncio.gather()` is used to run `greet("Alice")`, `greet("Bob")`, and `greet("Charlie")` concurrently.
   
3. `await asyncio.gather(...)` pauses the `main` function until all greetings are done.

__Handling Asynchronous Functions with__ `asyncio.create_task`

You can use `asyncio.create_task` to schedule the execution of coroutines and manage them as tasks.

    import asyncio

    async def fetch_data():
        print("Start fetching data")
        await asyncio.sleep(2)
        print("Done fetching data")
        return {"data": 123}

    async def main():
        task = asyncio.create_task(fetch_data())

        # Perform other operations while the data is being fetched
        print("Performing other operations")
        await asyncio.sleep(1)
        print("Still working...")

        # Await the task result
        result = await task
        print(f"Result: {result}")

    asyncio.run(main())

__Explanation:__

1. `fetch_data()` simulates a data fetching operation with a 2-second delay.
   
2. `asyncio.create_task(fetch_data())` schedules fetch_data to run concurrently as a task.
   
3. While `fetch_data` is running, other operations are performed (`"Performing other operations"` and `"Still working..."`).
   
4. `await task` waits for `fetch_data` to complete and retrieves its result.

## Combining Asynchronous Functions

You can combine multiple asynchronous functions to create more complex asynchronous workflows.

    import asyncio

    async def fetch_data():
        print("Fetching data...")
        await asyncio.sleep(1)
        return "data"

    async def process_data(data):
        print(f"Processing {data}...")
        await asyncio.sleep(1)
        return "processed data"

    async def main():
        data = await fetch_data()
        processed_data = await process_data(data)
        print(f"Final result: {processed_data}")

    asyncio.run(main())

__Explanation:__

1. `fetch_data()` fetches data with a 1-second delay.
   
2. `process_data(data)` processes the fetched data with a 1-second delay.
   
3. `main()` orchestrates the fetching and processing by awaiting the results of both functions in sequence.

- These examples demonstrate how to define and manage asynchronous functions using the `async` and `await` keywords in Python. By using these tools, you can write non-blocking code that performs multiple tasks concurrently, improving the efficiency and responsiveness of your programs.

## How to Execute an Async Program with `asyncio`

The `asyncio` module provides a framework for writing asynchronous programs in Python. It includes support for coroutines, tasks, and event loops.

__Example__

    import asyncio

    async def say_hello():
        print("Hello")
        await asyncio.sleep(1)
        print("World")

    # Running the async program
    asyncio.run(say_hello())

- This program will print `"Hello"`, wait for ``one second``, and then print `"World"`.

## How to Run Concurrent Coroutines

You can run multiple coroutines concurrently using `asyncio.gather()` or `asyncio.create_task()`.

__Example with `asyncio.gather()`__

    import asyncio

    async def task1():
        await asyncio.sleep(1)
        print("Task 1 completed")

    async def task2():
        await asyncio.sleep(2)
        print("Task 2 completed")

    async def main():
        await asyncio.gather(task1(), task2())

    asyncio.run(main())

In this example, `task1` and `task2` run concurrently, and the total execution time is the longest of the two, i.e., 2 seconds.

## How to Create asyncio Tasks

Tasks are used to schedule coroutines concurrently. A task is created using `asyncio.create_task()`.

__Example__

    import asyncio

    async def my_task():
        await asyncio.sleep(1)
        print("Task executed")

    async def main():
        task = asyncio.create_task(my_task())
        await task

    asyncio.run(main())

Here, `my_task` is created as a task and scheduled to run concurrently within the `main` coroutine.

## How to Use the `random` Module

The `random` module in Python provides a suite of functions to generate random numbers and perform random operations. This module is commonly used for tasks that require randomness, such as simulations, games, and randomized algorithms.

__Example with Asynchronous Code__

    import asyncio
    import random

    async def random_sleep():
        sleep_time = random.randint(1, 5)
        await asyncio.sleep(sleep_time)
        print(f"Slept for {sleep_time} seconds")

    async def main():
        await asyncio.gather(random_sleep(), random_sleep(), random_sleep())

    asyncio.run(main())

- In this example, `random.randint(1, 5)` is used to generate a random sleep time between 1 and 5 seconds for each `random_sleep` coroutine.

## Another Example Usage in an Asynchronous Program

Using the `random` module within an asynchronous program can help simulate delays, randomize tasks, or generate random data.

__Example: Asynchronous Task with Random Delays__

    import asyncio
    import random

    async def random_delay_task(name):
        delay = random.uniform(0.5, 2.0)
        print(f"Task {name} will sleep for {delay:.2f} seconds.")
        await asyncio.sleep(delay)
        print(f"Task {name} is done sleeping.")

    async def main():
        tasks = [random_delay_task(i) for i in range(5)]
    await asyncio.gather(*tasks)

    asyncio.run(main())

__Explanation__:

1. `random.uniform(0.5, 2.0)` generates a random delay between 0.5 and 2.0 seconds.

2. `await asyncio.sleep(delay)` pauses the task for the random delay.

3. `asyncio.gather(*tasks)` runs all tasks concurrently.

__Example: Randomly Select Tasks to Execute__

    import asyncio
    import random

    async def task(name):
        print(f"Task {name} is running.")
        await asyncio.sleep(1)
        print(f"Task {name} is complete.")

    async def main():
        tasks = [task(i) for i in range(10)]
        selected_tasks = random.sample(tasks, 5)
        await asyncio.gather(*selected_tasks)

    asyncio.run(main())

__Explanation:__

1. `random.sample(tasks, 5)` selects 5 random tasks from the list of 10 tasks.

2.`asyncio.gather(*selected_tasks)` runs the selected tasks concurrently.

By combining the `random` module with asynchronous programming, you can create more dynamic and varied behaviors in your programs, making them more flexible and realistic for simulations and testing scenarios.











