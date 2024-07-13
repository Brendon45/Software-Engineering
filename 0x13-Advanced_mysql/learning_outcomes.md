# 0x00. MySQL advanced

## Back-end

## SQL

## MySQL

### Definitions

## Creating Tables with Constraints

Creating tables with constraints involves defining rules and limitations on the data that can be stored in a table. Constraints help ensure data integrity and consistency. Common types of constraints include:

- Primary Key: Uniquely identifies each row in a table.
- Foreign Key: Ensures referential integrity between two tables.
- Unique: Ensures all values in a column are unique.
- Check: Ensures all values in a column satisfy a specific condition.
- Not Null: Ensures a column cannot have a NULL value.

## Optimizing Queries by Adding Indexes

Indexes are special data structures that improve the speed of ```data retrieval``` operations on a database table. Types of indexes include:

- ``Single Column Index:`` Index on a single column to speed up queries involving that column.
- ``Composite Index:`` Index on multiple columns to speed up queries involving those columns.
- ``Unique Index:`` Ensures all values in the indexed column are unique.
- ``Full-Text Index:`` Optimizes text searching within a column.

## Stored Procedures and Functions

- ``Stored Procedure:`` A set of SQL statements that can be executed as a unit, often used to encapsulate complex business logic.

- ``Function:`` Similar to stored procedures but can return a single value and are often used in SQL statements.

## Views

- Views are virtual tables created by querying one or more tables. They provide a simplified representation of data, which can help in managing complex queries.

## Triggers

- Triggers are database objects that automatically execute a specified set of SQL statements when certain events occur in the database (e.g., ``INSERT``, ``UPDATE``, ``DELETE``).