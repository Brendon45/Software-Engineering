# 0x02. Redis basic

## Back-end

## Redis

## Resources

__Read or watch:__

- [Redis Crash Course Tutorial](https://www.youtube.com/watch?v=Hbt56gFj998)
- [Redis commands](https://redis.io/docs/latest/commands/)
- [Redis python client](https://redis-py.readthedocs.io/en/stable/)
- [How to Use Redis With Python](https://realpython.com/python-redis/)

## What is Redis?

- Redis (`REmote DIctionary Server`) is an in-memory data structure store that can be used as a database, cache, and message broker. It supports various data structures such as strings, hashes, lists, sets, and more. Redis is known for its high performance, flexibility, and ease of use.

## Redis Commands

Here are some basic Redis commands:

- __SET key value__: Set the value of a key.

- __GET key__: Get the value of a key.

- __DEL key__: Delete a key.

- __EXISTS key__: Check if a key exists.

- __EXPIRE key seconds__: Set a timeout on a key.

- __INCR key__: Increment the value of a key by one.

- __LPUSH key value__: Prepend a value to a list.

- __RPUSH key value__: Append a value to a list.

- __LPOP key__: Remove and get the first element in a list.

- __RPOP key__: Remove and get the last element in a list.

- __SADD key value__: Add a member to a set.

- __SMEMBERS key__: Get all members in a set.

- __HSET key field value__: Set the value of a hash field.

- __HGET key field__: Get the value of a hash field.

## Explanation of the Redis with Python Code

Let's go through the code step by step to understand how Redis can be used for basic operations and as a simple cache in Python.

## 1. Connecting to Redis

First, you need to establish a connection to the Redis server using the `redis-py` library.

__Code:__

    import redis

    # Connect to the local Redis server
    r = redis.Redis(host='localhost', port=6379, db=0)

- `import redis`: Imports the `redis` module, which allows you to interact with a Redis server.
- `r = redis.Redis(host='localhost'`, `port=6379`, `db=0)`: Creates a connection to the Redis server running on `localhost` at port `6379`, using database `0`.

## 2. Basic Operations

__Set and Get__

    # Set a key-value pair
    r.set('name', 'Alice')

    # Get the value of the key
    name = r.get('name')
    print(name.decode())  # Output: Alice

- `r.set('name', 'Alice')`: Stores the value `'Alice'` under the key `'name'` in Redis.
- `name = r.get('name')`: Retrieves the value stored under the key `'name'`.
- `name.decode()`: Converts the byte string returned by Redis into a regular string.

__Increment__

    # Set a key with an initial value
    r.set('counter', 0)

    # Increment the value of the key
    r.incr('counter')
    counter_value = r.get('counter')
    print(counter_value.decode())  # Output: 1

- `r.set('counter', 0)`: Initializes a key `'counter'` with the value `0`.

- `r.incr('counter')`: Increments the value of `'counter'` by 1.
  
- `counter_value` = `r.get('counter')`: Retrieves the incremented value.

- `counter_value.decode()`: Converts the byte string to a regular string.

__Lists__

    # Push elements to a list
    r.lpush('mylist', 'one')
    r.rpush('mylist', 'two')

    # Pop elements from a list
    left_item = r.lpop('mylist')
    right_item = r.rpop('mylist')
    print(left_item.decode())  # Output: one
    print(right_item.decode())  # Output: two

- `r.lpush('mylist', 'one')`: Pushes the element `'one'` to the left of the list `'mylist'`.

- `r.rpush('mylist', 'two')`: Pushes the element `'two'` to the right of the list `'mylist'`.

- `left_item = r.lpop('mylist')`: Pops the leftmost element from `'mylist'`.

- `right_item = r.rpop('mylist')`: Pops the rightmost element from `'mylist'`.

- `left_item.decode()` and `right_item.decode()`: Convert the byte strings to regular strings.

__Sets__

    # Add elements to a set
    r.sadd('myset', 'a')
    r.sadd('myset', 'b')

    # Get all elements from a set
    set_members = r.smembers('myset')
    print(set_members)  # Output: {b'a', b'b'}

- `r.sadd('myset', 'a')` and `r.sadd('myset', 'b')`: Add elements `'a'` and `'b'` to the set `'myset'`.
  
- `set_members = r.smembers('myset')`: Retrieves all members of the set `'myset'`.

- `print(set_members)`: Prints the set members as byte strings.

__Hashes__

    # Set a field in a hash
    r.hset('myhash', 'field1', 'value1')

    # Get a field from a hash
    field_value = r.hget('myhash', 'field1')
    print(field_value.decode())  # Output: value1

- `r.hset('myhash', 'field1', 'value1')`: Sets the field `'field1'` in the hash `'myhash'` to the value `'value1'`.

- `field_value = r.hget('myhash', 'field1')`: Retrieves the value of the field `'field1'` from the hash `'myhash'`.

- `field_value.decode()`: Converts the byte string to a regular string.

__Expiration__

    # Set a key with an expiration time (in seconds)
    r.set('temp', 'value', ex=5)

    # Check the remaining time to live
    ttl = r.ttl('temp')
    print(ttl)  # Output: 5 (or less, as time passes)

- `r.set('temp', 'value', ex=5)`: Sets the key `'temp'` to the value `'value'` with an expiration time of 5 seconds.
  
- `ttl = r.ttl('temp')`: Gets the remaining time to live for the key `'temp'`.
  
- `print(ttl)`: Prints the TTL value.

## Using Redis as a Simple Cache

Redis can be used to cache expensive computations or frequently accessed data to improve performance.

__Caching Function Results__

1. ___Define Functions to Interact with Cache___

        import redis
        import time

        # Connect to Redis
        r = redis.Redis(host='localhost', port=6379, db=0)

        def get_data_from_cache(key):
            # Try to get data from Redis cache
            data = r.get(key)
            if data is None:
                return None
            return data.decode()

        def set_data_to_cache(key, value, expiration=60):
            # Set data to Redis cache with an expiration time
            r.set(key, value, ex=expiration)

         def expensive_function(param):
             # Simulate a time-consuming function
             time.sleep(2)
             return f"Result for {param}"

        def get_data(param):
            # Check cache first
            cached_data = get_data_from_cache(param)
            if cached_data:
                print("Cache hit")
                return cached_data
    
          print("Cache miss")
          # Compute the data if not in cache
          result = expensive_function(param)
          # Store the result in cache
          set_data_to_cache(param, result)
          return result

- `get_data_from_cache(key)`: Attempts to retrieve the value associated with `key` from Redis. If the key does not exist, returns `None`.

- `set_data_to_cache(key, value, expiration=60)`: Stores `value` in Redis under `key` with an expiration time (default is 60 seconds).

- `expensive_function(param)`: Simulates a time-consuming function by sleeping for 2 seconds and then returning a result string.

- `get_data(param)`: First checks if the data is in the cache. If it is, it returns the cached data. If not, it calls `expensive_function`, caches the result, and then returns it.

2. __Example Usage__

        # Example usage
        param = "test"
        print(get_data(param))  # Cache miss, computes the result
        print(get_data(param))  # Cache hit, retrieves from cache

- `get_data(param)`: First call will be a cache miss and compute the result. The second call will be a cache hit and return the cached result.

__Caching with Expiration__

    # Set data to Redis cache with an expiration time
    set_data_to_cache('key_with_expiry', 'value', expiration=10)

    # Wait for expiration
    time.sleep(10)

      # Attempt to get the data from cache after expiration
      expired_data = get_data_from_cache('key_with_expiry')
      print(expired_data)  # Output: None (data has expired)

__Explanation:__

- `set_data_to_cache('key_with_expiry'`, `'value', expiration=10)`: Stores `'value'` under `'key_with_expiry' `with an expiration time of 10 seconds.

- `time.sleep(10)`: Waits for 10 seconds to let the key expire.

- `expired_data = get_data_from_cache('key_with_expiry')`: Attempts to retrieve the value after expiration. It should return `None` as the key has expired.

### Summary

1. __Connecting to Redis__: Use redis-py to connect to a Redis server.

2. __Basic Operations__: Set and get values, increment counters, work with lists, sets, and hashes, and set expiration times.

3. __Caching__: Cache expensive computations or frequently accessed data to improve performance.

4. __Expiration__: Set keys with expiration times to automatically remove them after a certain period.

By following these steps and examples, you can effectively leverage Redis for both `basic operations` and as a `caching layer` in your `Python applications`.
