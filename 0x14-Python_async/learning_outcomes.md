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

## `async` and `awai` Syntax

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







