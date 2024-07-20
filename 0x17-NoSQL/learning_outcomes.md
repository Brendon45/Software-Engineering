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
