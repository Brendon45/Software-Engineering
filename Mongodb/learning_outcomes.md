"""
MongoDB
=======
- MongoDB is a NoSQL database that stores data in JSON-like documents.
- Technically it is BSON (Binary JSON) format.
- It is a document-oriented database, which means that it stores data in the form of documents.

Data Types
==========
- String: This is used to store text.
- Integer: This is used to store whole numbers.
- Arrays: This is used to store arrays or lists.
- Boolean: This is used to store true or false values.
- Double: This is used to store floating-point numbers.
- Object: This is used to store embedded documents.
- Null: This is used to store null values.
- Date: This is used to store date and time.
- Timestamp: This is used to store timestamp.
- Object ID: This is used to store the document's ID.
- Binary Data: This is used to store binary data.
- Regular Expression: This is used to store regular expressions.

Document
========
- A document is a set of key-value pairs.
- A document is similar to a row in a relational database.
- A document is stored in a collection.

Example:
========
{
  "name": "John Doe",
  "age": 25,
  "city": "New York"
}

Collection
==========
- A collection is a group of one or more documents.
- A collection is similar to a table in a relational database.

Example:
========
{
  "name": "John Doe",
  "age": 25,
  "city": "New York"
}
{
  "name": "Jane Doe",
  "age": 30,
  "city": "Los Angeles"
}

Database
========
- A database is a group of one or more collections.
- A database is similar to a database in a relational database.
- This makes scaling and working with our database easier.

Example:
=======
Database: mydb

-------------

To create a database in MongoDB, we use the following command:
==============================================================

use <database_name> :This creates the database if it does not exist, otherwise, it switches to the existing database.
show dbs :This command shows all the databases in the MongoDB server.

-------------

After switching to the database, we can create a collection and insert documents into it.

To create a collection in MongoDB, we use the following command:
================================================================

db.createCollection("<collection_name>") :This creates a collection in the current database.
show collections :This command shows all the collections in the current database.

-------------

To drop a database in MongoDB, we use the following command:
============================================================

First, we need to switch to the database that we want to drop.

db.dropDatabase() :This command drops the current database.

-------------

To insert documents into a MongoDB database:
============================================

First switch to the database you want to use

use <database_name>;

db.<collection_name>.insertOne({})  :This inserts only one document into the collection.

If the collection doesn't exist, one will be created.
Inside the () is the document aka {} and then inside the document we have the
key: value pair

Example:
========

use school;

db.students.insertOne({name: "Tafara", isStudent: true, age: 100})

If the query was successful, you will get:

{
  acknowledged: true,
  insertedId: ObjectId('66918d783e3afcf5b0482f8b')
}

OR

db.students.insertOne({name: "Harry",
                        age: 16,
                        marks: 2.8,
                        fullTime: true,
                        registerDate: new Date(),
                        graduationDate: null,
                        courses: ["History", "Computer Science", "Python"],
                        address: {street: "4 Privet Drive",
                                    city: "London",
                                    country: "UK",
                                    zip: 12345}
                                    })


If we want to return all the documents in a collection:
=======================================================

db.<collection_name>.find()

[
  {
    _id: ObjectId('66918d783e3afcf5b0482f8b'),
    name: 'Tafara',
    age: 100,
    isStudent: true
  }
]

If we want to insert more than one document into a collection:
==============================================================

db.<collection_name>.insertMany([{}, {}, {}])

Here we are inserting 3 documents into the collection, each document is separated
by a comma and the documents are enclosed in square brackets or an array.

Example:
========

db.students.insertMany([
    {
        name: "Tinotenda",
        isStudent: true,
        age: 30
    },
    {
        name: "Tafadzwa",
        isStudent: true,
        age: 1000
    },
    {
        name: "Amahle",
        isStudent: true,
        age: 50
    }
])

Another Example:
================
db.movies.insertMany([
   {
      title: "Jurassic World: Fallen Kingdom",
      genres: [ "Action", "Sci-Fi" ],
      runtime: 130,
      rated: "PG-13",
      year: 2018,
      directors: [ "J. A. Bayona" ],
      cast: [ "Chris Pratt", "Bryce Dallas Howard", "Rafe Spall" ],
      type: "movie"
    },
    {
      title: "Tag",
      genres: [ "Comedy", "Action" ],
      runtime: 105,
      rated: "R",
      year: 2018,
      directors: [ "Jeff Tomsic" ],
      cast: [ "Annabelle Wallis", "Jeremy Renner", "Jon Hamm" ],
      type: "movie"
    }
])

If we want to drop a collection in MongoDB:
===========================================

db.<collection_name>.drop()

If we want to drop a document in a collection:
==============================================

db.<collection_name>.deleteOne({}) :This deletes only one document in the collection.

Example:
========

db.students.deleteOne({ name: "Tafara"})

SORTING
=======
By default, MongoDB uses the _id field to sort the documents in a collection.

If we want to sort the documents in a collection:
=================================================

db.<collection_name>.find().sort({key: 1}) :This sorts the documents in ascending order.
db.<collection_name>.find().sort({key: -1}) :This sorts the documents in descending order.

LIMITING
========

If we want to limit the number of documents returned:
=====================================================

db.<collection_name>.find().limit(2) :This limits the number of documents returned to 2.

We can also SORT and LIMIT the documents in a collection:
=========================================================

db.<collection_name>.find().sort({key: 1}).limit(2) :This sorts the documents in ascending order and limits the number of documents returned to 2.

Using the find() method:
========================

db.<collection_name>.find({key: value}) :This returns all the documents in the collection where the key has the value.

To apply multiple conditions:
=============================

db.<collection_name>.find({key1: value1, key2: value2}) :This returns all the documents in the collection where key1 has value1 and key2 has value2.

To return only specific fields:
===============================

db.<collection_name>.find({}, {key1: 1, key2: 1}) :This returns only the key1 and key2 fields in the documents.

Example:
========

db.students.find({}, {name: true}) : This returns only the name field in the documents.

db.students.find({}, {_id: false, name: true, age: true}) : This returns only the name and age fields in the documents and disables the _id field.

If we want to disable the _id field:
====================================

db.<collection_name>.find({}, {_id: false}) :This disables the _id field in the documents.

We can use 0 = false and 1 = true.

UPDATING
========

To update one document:

db.<collection_name>.updateOne({key: value}, {$set: {key: value}}) :This updates one document in the collection.

Example:
========

db.students.updateOne({name: "Tafara"}, {$set: {age: 101}})

The same syntax is used to add key: value pairs if they don't exist in a document(s):
=====================================================================================

db.students.updateOne({name: "Tafara"}, {$set: {marks: 90}})  : This adds the marks key: value pair to the document, if it exists it will update the value.


As our our data gets too big, it's possible that we will have keys that are not unique or the same.

So now it's much safer if we filter by the _id field as it is unique for each document.

db.students.updateOne({_id: ObjectId('66918d783e3afcf5b0482f8b')}, {$set: {marks: 90}})

To update more than one document:
=================================

db.<collection_name>.updateMany({key: value}, {$set: {key: value}}) :This updates more than one document in the collection.

Example:
========
db.students.updateMany({}, {$set: {age: 101}})  : This updates the age key: value pair in all the documents in the collection.
db.students.updateMany({zip: 0000}, {$set: {age: 101}})  : This updates the age key: value pair in all the documents in the collection where the zip key has the value 0000.

We can to also check if a key: value pair exists in a document and set it if it doesn't:
========================================================================================
db.<collection>.updateMany({key: {$exists: false}}, {$set: {key: value}})  : This checks if a key is available on all the documents, if not it creates it and gives a value

Example:
========
db.students.updateMany({fullTime: {$exists: false}}, {$set: {fullTime: true}}) : This checks if the fullTime key exists in all the documents, if not it creates it and gives it the value true.


DELETING
========

If we want to remove a key: value pair from a document:
=======================================================

db.students.updateOne({name: "Tafara"}, {$unset: {marks: 1}}) :This removes the marks key: value pair from the document.

We can use 1, true or "" to remove a key: value pair.

OR

db.<collection>.update
(
   { _id: ObjectId("65f8b8499abfc382ebcd9668") },
   { $unset: { key: "" } }
)

To delete one document:
=======================

db.<collection>.deleteOne({key: value})  : This deletes one document in the collection.

Example:
========

db.<collection>.deleteOne({name: "Tafara"})  : This deletes the document where the name key has the value Tafara.


To delete more than one document:
=================================

db.<collection>.deleteMany({key: value})  : This deletes more than one document in the collection.

Example:
========
db.students.deleteMany({age: 100})  : This deletes all the documents where the age key has the value 100.

db.students.deleteMany({age: {$gt: 100}})  : This deletes all the documents where the age key has a value greater than 100.

db.students.deleteMany({key: {$exists: false}})  : This deletes all the documents where the key does not exist.

COMPARISON QUERY OPERATORS
==========================

$eq : This is used to check if a key has a value.
$gt : This is used to check if a key has a value greater than.
$gte : This is used to check if a key has a value greater than or equal to.
$lt : This is used to check if a key has a value less than.
$lte : This is used to check if a key has a value less than or equal to.
$ne : This is used to check if a key does not have a value.
$in : This is used to check if a key has a value in an array.
$nin : This is used to check if a key does not have a value in an array.
$exists : This is used to check if a key exists in a document.
$regex : This is used to check if a key matches a regular expression.

Example:
========

$eq
===
If we want to find documents where the key has a specific value:

db.<collection>.find({key: value}) : This returns all the documents where the key has the specified value.

db.students.find({age: 100})  : This returns all the documents where the age key has the value 100.

$ne
===
If we want to find any other matches except for a specific value:

db.<collection>.find({key: {$ne: value}}) : This returns all the documents where the key does not have the specified value.

db.students.find({age: {$ne: 100}})  : This returns all the documents where the age key does not have the value 100.

$lt
===
If we want to find documents where the key has a value less than:

db.<collection>.find({key: {$lt: value}}) : This returns all the documents where the key has a value less than the specified value.

db.students.find({age: {$lt: 100}})  : This returns all the documents where the age key has a value less than 100.

$in
===
If we want to find documents where the key has a value in an array:

db.<collection>.find({key: {$in: [value1, value2]}}) : This returns all the documents where the key has a value in the specified array.

db.students.find({age: {$in: [100, 200]}})  : This returns all the documents where the age key has a value of 100 or 200.

$nin
====
If we want to find documents where the key does not have a value in an array:

db.<collection>.find({key: {$nin: [value1, value2]}}) : This returns all the documents where the key does not have a value in the specified array.

db.students.find({age: {$nin: [100, 200]}})  : This returns all the documents where the age key does not have a value of 100 or 200.


We can use multiple comparison query operators in a query:
==========================================================

db.<collection>.find({key1: {$gt: value1}, key2: {$lt: value2}}) : This returns all the documents where key1 has a value greater than value1 and key2 has a value less than value2.

db.students.find({age: {$gt: 100}, age: {$lt: 200}})  : This returns all the documents where the age key has a value greater than 100 and less than 200.
OR
db.students.find({age: {$gt: 100, $lt: 200}})  : This returns all the documents where the age key has a value greater than 100 and less than 200.


LOGICAL QUERY OPERATORS
=======================

$and : This is used to combine multiple conditions.
    All the conditions must be true for the document to be returned.
    Returns all documents that match all the conditions.

$or : This is used to check if any of the conditions are true.
    At least one of the conditions must be true for the document to be returned.
    Returns all documents that match at least one of the conditions.

$nor : This is used to check if none of the conditions are true.
    None of the conditions must be true for the document to be returned.
    It is the opposite of the $and operator.
    Returns all documents that do not match any of the conditions.

$not : This is used to negate a condition.
    Returns all documents that do not match the condition.

Example:
========

$and
====
If we want to find documents where multiple conditions are true:

db.<collection>.find({$and: [{key1: value1}, {key2: value2}]}) : This returns all the documents where key1 has value1 and key2 has value2.

db.students.find({$and: [{age: 100}, {isStudent: true}]})  : This returns all the documents where the age key has the value 100 and the isStudent key has the value true.

db.students.find({$and: [{name: "Tafara"}, {married: false}]})  : This returns all the documents where the name key has the value Tafara and the married key has the value false.

$or
===
If we want to find documents where at least one condition is true:

db.<collection>.find({$or: [{key1: value1}, {key2: value2}]}) : This returns all the documents where key1 has value1 or key2 has value2.

db.students.find({$or: [{age: 100}, {isStudent: true}]})  : This returns all the documents where the age key has the value 100 or the isStudent key has the value true.

db.students.find({$or: [{name: "Tafara"}, {married: false}]})  : This returns all the documents where the name key has the value Tafara or the married key has the value false.

$nor
====
If we want to find documents where none of the conditions are true:

db.<collection>.find({$nor: [{key1: value1}, {key2: value2}]}) : This returns all the documents where key1 does not have value1 and key2 does not have value2.

db.students.find({$nor: [{age: 100}, {isStudent: true}]})  : This returns all the documents where the age key does not have the value 100 and the isStudent key does not have the value true.

db.students.find({$nor: [{name: "Tafara"}, {married: false}]})  : This returns all the documents where the name key does not have the value Tafara and the married key does not have the value false.

$not
====
If we want to find documents that do not match a condition:

db.<collection>.find({key: {$not: {value}}}) : This returns all the documents where the key does not have the specified value.

db.students.find({age: {$not: 100}})  : This returns all the documents where the age key does not have the value 100.

db.students.find({name: {$not: "Tafara"}})  : This returns all the documents where the name key does not have the value Tafara.

db.students.find({age: {$not: {$gte: 30}}})  : This returns all the documents where the age key does not have a value greater than or equal to 30.


"""