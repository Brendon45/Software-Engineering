# 0x00. MySQL advanced

## Back-end

## SQL

## MySQL

### Definitions

## Creating Tables with Constraints

Creating tables with constraints involves defining rules and limitations on the data that can be stored in a table. Constraints help ensure data integrity and consistency. Common types of constraints include:

- ``Primary Key:`` Uniquely identifies each row in a table.
- ``Foreign Key:`` Ensures referential integrity between two tables.
- ``Unique:`` Ensures all values in a column are unique.
- ``Check:`` Ensures all values in a column satisfy a specific condition.
- ``Not Null:`` Ensures a column cannot have a NULL value.

## Examples of Creating Tables with Constraints:

1. Primary Key

        CREATE TABLE users (
         id INT AUTO_INCREMENT PRIMARY KEY,
         email VARCHAR(255) NOT NULL UNIQUE,
         name VARCHAR(255),
         country ENUM('US', 'CO', 'TN') DEFAULT 'US' NOT NULL
        );

This code creates a table named users with:

- `id:` An auto-incrementing integer that uniquely identifies each user.

- `email:` A unique, non-nullable string to store user email addresses.

- `name:` A string to store user names.

- `country:` An enumeration with default value 'US', restricting entries to 'US', 'CO', or 'TN'.

2. Foreign Key

        CREATE TABLE orders (
         order_id INT AUTO_INCREMENT PRIMARY KEY,
         user_id INT,
         FOREIGN KEY (user_id) REFERENCES users(id)
        );
   
This code creates a table named orders with:

- `order_id:` An auto-incrementing integer serving as the primary key.
- `user_id:` An integer referencing the id field in the users table, establishing a relationship between orders and users.

3. Unique Constraint

        CREATE TABLE products (
         product_id INT AUTO_INCREMENT PRIMARY KEY,
         product_name VARCHAR(255) NOT NULL UNIQUE
        );

This code creates a table named products with:

- `product_id:` An auto-incrementing integer serving as the primary key.
- `product_name:` A unique, non-nullable string to store product names.

4. Check Constraint

        CREATE TABLE employees (
         emp_id INT AUTO_INCREMENT PRIMARY KEY,
         age INT,
         CHECK (age >= 18)
        );

This code creates a table named employees with:

- `emp_id:` An auto-incrementing integer serving as the primary key.
- `age:` An integer that must be 18 or older.

5. Not Null Constraint

        CREATE TABLE orders (
         order_id INT AUTO_INCREMENT PRIMARY KEY,
         order_date DATE NOT NULL
        );
   
This code creates a table named orders with:

- `order_date:` A non-nullable date, ensuring every order has a date.

## Optimizing Queries by Adding Indexes

Indexes are special data structures that improve the speed of ```data retrieval``` operations on a database table. Types of indexes include:

- ``Single Column Index:`` Index on a single column to speed up queries involving that column.
- ``Composite Index:`` Index on multiple columns to speed up queries involving those columns.
- ``Unique Index:`` Ensures all values in the indexed column are unique.
- ``Full-Text Index:`` Optimizes text searching within a column.

## Examples of Optimizing Queries by Adding Indexes:

1. Single Column Index

        CREATE INDEX idx_user_email ON users(email);

- This creates an index on the `email` column in the `users` table, speeding up queries filtering by email.

2. Composite Index

        CREATE INDEX idx_user_name_country ON users(name, country);

- This creates an index on the `name` and `country` columns, optimizing queries filtering by both.

3. Unique Index

        CREATE UNIQUE INDEX idx_unique_email ON users(email);

- This ensures all values in the `email` column are unique.

4. Full-Text Index

        CREATE FULLTEXT INDEX idx_fulltext_name ON users(name);

- This creates a full-text index on the `name` column, optimizing text searches.

5. Dropping an Index

        DROP INDEX idx_user_email ON users;

- This removes the index on the `email` column in the `users` table.

## Stored Procedures and Functions

- ``Stored Procedure:`` A set of SQL statements that can be executed as a unit, often used to encapsulate complex business logic.

- ``Function:`` Similar to stored procedures but can return a single value and are often used in SQL statements.

## Examples of Stored Procedures and Functions

1. Stored Procedure

        DELIMITER //
        CREATE PROCEDURE GetUser(IN user_id INT)
        BEGIN
          SELECT * FROM users WHERE id = user_id;
        END //
        DELIMITER ;

        -- Call the procedure
        CALL GetUser(1);

- This stored procedure retrieves all columns from the `users` table for a given `user_id`.

2. Function

        DELIMITER //
        CREATE FUNCTION GetUserName(user_id INT) RETURNS VARCHAR(255)
        BEGIN
           DECLARE name VARCHAR(255);
          SELECT name INTO name FROM users WHERE id = user_id;
          RETURN name;
        END //
        DELIMITER ;

        -- Use the function
        SELECT GetUserName(1);

- This function returns the `name` of a user given their `user_id`.

## Views

- Views are virtual tables created by querying one or more tables. They provide a simplified representation of data, which can help in managing complex queries.

## Examples of Views

1. Creating a View

        CREATE VIEW UserEmails AS
        SELECT id, email FROM users;

        -- Query the view
        SELECT * FROM UserEmails;

- This creates a view named `UserEmails` that selects the `id` and email columns from the `users` table.

2. Updating a View

        CREATE VIEW UserDetails AS
        SELECT id, name, email FROM users;

        -- Update the view
        UPDATE UserDetails SET email = 'newemail@example.com' WHERE id = 1;

- This creates a view named `UserDetails` and allows updates to the underlying data.

3. Dropping a View

        DROP VIEW UserEmails;

- This removes the `UserEmails` view.

## Triggers

- Triggers are database objects that automatically execute a specified set of SQL statements when certain events occur in the database (e.g., ``INSERT``, ``UPDATE``, ``DELETE``).
