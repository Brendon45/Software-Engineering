# 0x01. NoSQL

## Back-end

## NoSQL

## MongoDB

## Resources

__Read or watch:__

- [NoSQL Databases Explained](https://riak.com/resources/nosql-databases/)
- [What is NoSQL ?](https://www.youtube.com/watch?v=qUV2j3XBRHc)
- [MongoDB with Python Crash Course - Tutorial for Beginners](https://www.youtube.com/watch?v=E-1xI85Zog8)
- [MongoDB Tutorial 2 : Insert, Update, Remove, Query](https://www.youtube.com/watch?v=CB9G5Dvv-EE)
- [Aggregation](https://www.mongodb.com/docs/manual/aggregation/)
- [Introduction to MongoDB and Python](https://realpython.com/introduction-to-mongodb-and-python/)
- [mongo Shell Methods](https://www.mongodb.com/docs/manual/reference/method/)
- [Mongosh](https://www.mongodb.com/docs/mongodb-shell/#mongodb-binary-bin.mongosh)

## What is NoSQL?

- NoSQL stands for `"Not Only SQL"` and represents a class of database management systems that do not follow the traditional relational database model.
- NoSQL databases are designed to handle large volumes of `unstructured`, `semi-structured`, and `structured` data. They provide a mechanism for storage and retrieval of data that is modeled differently from tabular relations used in relational databases.

## Differences Between SQL and NoSQL

### 1. Data Model:

- __SQL:__ Uses structured query language (SQL) for defining and manipulating data. Data is stored in tables with a fixed schema.
- __NoSQL:__ Data can be stored in various formats like document, key-value, graph, and column. Schema-less or dynamic schema.

### 2. Scalability:

- __SQL:__ Typically scales vertically by adding more power (CPU, RAM) to the existing server.

- __NoSQL:__ Designed to scale horizontally by adding more servers to the distributed system.

### 3. Flexibility:

- __SQL:__ Requires a predefined schema and structure.

- __NoSQL:__ Offers flexible schemas, allowing for changes in data structure without major disruptions.

### 4. Transactions:

- __SQL:__ Strong support for ACID (Atomicity, Consistency, Isolation, Durability) transactions.

- __NoSQL:__ Varies; some provide ACID compliance, while others offer eventual consistency for better performance and scalability.

## What is ACID?

__ACID__ is a set of properties that guarantee reliable processing of database transactions:

- __Atomicity:__ Ensures that all operations within a transaction are completed successfully; if not, the transaction is aborted.

- __Consistency:__ Ensures that the database remains in a consistent state before and after the transaction.

- __Isolation:__ Ensures that transactions are executed independently, without interference from other transactions.

- __Durability:__ Ensures that once a transaction is committed, it will remain so, even in the event of a system failure.

## What is Document Storage?

__Document storage__ is a type of NoSQL database that stores data as documents, typically in JSON, BSON, or XML format. Each document can have a unique structure, allowing for flexibility and the ability to store complex nested data.

## Types of NoSQL Databases

1. __Document Databases:__ Store data as documents (`e.g., MongoDB, CouchDB`).

2. __Key-Value Stores:__ Store data as key-value pairs (`e.g., Redis, DynamoDB`).

3. __Column-Family Stores:__ Store data in columns rather than rows (`e.g., Apache Cassandra, HBase`).

4. __Graph Databases:__ Store data as nodes and relationships (`e.g., Neo4j, OrientDB`).

## Benefits of NoSQL Databases

- __Scalability:__ Easily scales horizontally.

- __Flexibility:__ Allows for dynamic schema design.

- __Performance:__ Optimized for specific use cases like read-heavy or write-heavy applications.

- __Big Data:__ Handles large volumes of data efficiently.

## Querying Information from a NoSQL Database

- __Document Databases:__ Use document-based query languages.
 Example in MongoDB:

      db.collection.find({ "name": "Alice" })

## Inserting/Updating/Deleting Information from a NoSQL Database

- __Inserting:__

      db.collection.insert_one({ "name": "Alice", "age": 25 })

- __Updating:__

      db.collection.update_one({ "name": "Alice" }, { "$set": { "age": 26 } })

- __Deleting:__

      db.collection.delete_one({ "name": "Alice" })

## Mongosh

__Mongosh__ is the `MongoDB Shell`, a command-line interface for interacting with MongoDB instances. It provides a JavaScript-based environment to run database operations.

- __Start Mongosh:__

      mongosh

- __Basic Commands:__

      show dbs
      use mydatabase
      show collections

### Detailed Example with MongoDB and Python

1. __Connecting and Creating a Collection:__

       from pymongo import MongoClient

       client = MongoClient('mongodb://localhost:27017/')
       db = client.mydatabase
       collection = db.mycollection

__Explanation:__

- `from pymongo import MongoClient`: Imports the `MongoClient` class from the `pymongo` library.
  
- `client = MongoClient('mongodb://localhost:27017/')`: Creates a connection to the MongoDB server running on `localhost` at port `27017`.
  
- `db = client.mydatabase`: Accesses the database named `mydatabase`. If the database does not exist, it will be created when you insert the first document.
  
- `collection = db.mycollection`: Accesses the collection named `mycollection` within `mydatabase`. Like the database, if the collection does not exist, it will be created when the first document is inserted.

2. __Inserting Documents:__

       # Single document
       collection.insert_one({ "name": "Alice", "age": 25 })

       # Multiple documents
       collection.insert_many([
           { "name": "Bob", "age": 30 },
           { "name": "Charlie", "age": 35 }
       ])

__Explanation:__

- `collection.insert_one({ "name": "Alice", "age": 25 })`: Inserts a single document into the `mycollection` collection with fields `name` and `age`.

- `collection.insert_many([...])`: Inserts multiple documents into the `mycollection` collection. Each document in the list will be inserted as a separate record.

3. __Querying Documents:__

       # Find one document
       document = collection.find_one({ "name": "Alice" })
       print(document)

       # Find multiple documents
       for doc in collection.find({ "age": { "$gt": 25 } }):
           print(doc)

__Explanation:__

- `collection.find_one({ "name": "Alice" })`: Queries the `mycollection` collection for a single document where the `name` field is `"Alice"`. It returns the first matching document.

- `print(document)`: Prints the document retrieved by `find_one`.

- `collection.find({ "age": { "$gt": 25 } })`: Queries the `mycollection` collection for all documents where the `age` field is greater than 25 (`$gt` is a MongoDB query operator for "greater than").

- `for doc in collection.find({ "age": { "$gt": 25 } })`: Iterates over each document matching the query and prints it.

4. __Updating Documents:__

       # Update one document
       collection.update_one({ "name": "Alice" }, { "$set": { "age": 26 } })

       # Update multiple documents
       collection.update_many({ "age": { "$lt": 35 } }, { "$set": { "status": "active" } })

__Explanation:__

- `collection.update_one({ "name": "Alice" }, { "$set": { "age": 26 } })`: Finds the first document where the `name` field is `"Alice"` and updates the `age` field to `26`.

- `collection.update_many({ "age": { "$lt": 35 } }, { "$set": { "status": "active" } })`: Finds all documents where the `age` field is less than 35 and sets the `status` field to `"active"`.

5. __Deleting Documents:__

       # Delete one document
       collection.delete_one({ "name": "Alice" })

       # Delete multiple documents
       collection.delete_many({ "age": { "$lt": 35 } })
   
__Explanation:__

- `collection.delete_one({ "name": "Alice" })`: Deletes the first document where the `name` field is `"Alice"`.

- `collection.delete_many({ "age": { "$lt": 35 } })`: Deletes all documents where the `age` field is less than 35.

### Putting It All Together

This sequence of operations demonstrates how to perform basic CRUD (`Create, Read, Update, Delete`) operations with MongoDB using Python:

1. __Connecting to the Database__: Establishes a connection to the MongoDB server and accesses the database and collection.

2. __Inserting Documents__: Adds single or multiple documents to the collection.

3. __Querying Documents__: Retrieves documents based on specified criteria.

4. __Updating Documents__: Modifies existing documents based on specified criteria.

5. __Deleting Documents__: Removes documents based on specified criteria.

This comprehensive guide provides you with the foundational knowledge of `NoSQL databases`, their `types`, `benefits`, and how to perform basic operations using MongoDB and Python.
