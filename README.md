# MySQL Queries and Concepts
=====================================

## Table of Contents
-----------------

1. [Introduction](#introduction)
2. [Basic Queries](#basic-queries)
3. [Filtering Data](#filtering-data)
4. [Sorting and Limiting Data](#sorting-and-limiting-data)
5. [Joining Tables](#joining-tables)
6. [Subqueries](#subqueries)
7. [Grouping and Aggregating Data](#grouping-and-aggregating-data)
8. [Indexing and Optimizing Queries](#indexing-and-optimizing-queries)
9. [Database Design and Normalization](#database-design-and-normalization)
10. [Security and Access Control](#security-and-access-control)
11. [Transaction Control](#transaction-control)
12. [Views](#views)
13. [Stored Procedures](#stored-procedures)
14. [Triggers](#triggers)
15. [Constraints](#constraints)

## Introduction
------------

MySQL is a popular open-source relational database management system (RDBMS) that uses SQL (Structured Query Language) to manage and manipulate data. In this document, we will cover various MySQL queries and concepts with suitable examples.

### Basic Queries
----------------

#### SELECT Statement

The SELECT statement is used to retrieve data from a database table.

```sql
SELECT * FROM customers;
```

This query retrieves all columns (`*`) from the `customers` table.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

#### INSERT Statement

The INSERT statement is used to add new data to a database table.

```sql
INSERT INTO customers (name, email, phone)
VALUES ('John Doe', 'john.doe@example.com', '123-456-7890');
```

This query inserts a new row into the `customers` table with the specified values.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | John Doe | john.doe@example.com | 123-456-7890 |

#### UPDATE Statement

The UPDATE statement is used to modify existing data in a database table.

```sql
UPDATE customers
SET name = 'Jane Doe', email = 'jane.doe@example.com'
WHERE id = 1;
```

This query updates the `name` and `email` columns of the row with `id` = 1 in the `customers` table.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | Jane Doe | jane.doe@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

#### DELETE Statement

The DELETE statement is used to delete data from a database table.

```sql
DELETE FROM customers
WHERE id = 1;
```

This query deletes the row with `id` = 1 from the `customers` table.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 2  | Jane | jane@example.com | 987-654-3210 |

#### ALTER Statement

The ALTER statement is used to modify the structure of a database table.

```sql
ALTER TABLE customers
ADD COLUMN address VARCHAR(255);
```

This query adds a new column `address` to the `customers` table.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

| id | name | email | phone | address |
|----|------|-------|-------|---------|
| 1  | John | john@example.com | 123-456-7890 | NULL |
| 2  | Jane | jane@example.com | 987-654-3210 | NULL |

#### DROP Statement

The DROP statement is used to delete a database table.

```sql
DROP TABLE customers;
```

This query deletes the `customers` table.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

Table `customers` does not exist.

### Filtering Data
-----------------

#### WHERE Clause

The WHERE clause is used to filter data based on conditions.

```sql
SELECT * FROM customers
WHERE country = 'USA';
```

This query retrieves all rows from the `customers` table where the `country` column is 'USA'.

**Example Table:**

| id | name | email | phone | country |
|----|------|-------|-------|---------|
| 1  | John | john@example.com | 123-456-7890 | USA |
| 2  | Jane | jane@example.com | 987-654-3210 | Canada |

**Output:**

| id | name | email | phone | country |
|----|------|-------|-------|---------|
| 1  | John | john@example.com | 123-456-7890 | USA |

#### AND, OR, and NOT Operators

The AND, OR, and NOT operators are used to combine conditions in the WHERE clause.

```sql
SELECT * FROM customers
WHERE country = 'USA' AND age > 18;
```

This query retrieves all rows from the `customers` table where the `country` column is 'USA' and the `age` column is greater than 18.

**Example Table:**

| id | name | email | phone | country | age |
|----|------|-------|-------|---------|-----|
| 1  | John | john@example.com | 123-456-7890 | USA | 25 |
| 2  | Jane | jane@example.com | 987-654-3210 | Canada | 30 |

**Output:**

| id | name | email | phone | country | age |
|----|------|-------|-------|---------|-----|
| 1  | John | john@example.com | 123-456-7890 | USA | 25 |

### Sorting and Limiting Data
---------------------------

#### ORDER BY Clause

The ORDER BY clause is used to sort data in ascending or descending order.

```sql
SELECT * FROM customers
ORDER BY name ASC;
```

This query retrieves all rows from the `customers` table and sorts them in ascending order by the `name` column.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 2  | Jane | jane@example.com | 987-654-3210 |
| 1  | John | john@example.com | 123-456-7890 |

#### LIMIT Clause

The LIMIT clause is used to limit the number of rows retrieved. It is often used in conjunction with the ORDER BY clause to retrieve a specific number of rows in a specific order.

```sql
SELECT * FROM customers
ORDER BY name ASC
LIMIT 10;
```

This query retrieves the first 10 rows from the `customers` table, sorted in ascending order by the `name` column.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |
| 4  | Alice | alice@example.com | 901-234-5678 |
| 5  | Mike | mike@example.com | 111-222-3333 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 4  | Alice | alice@example.com | 901-234-5678 |
| 3  | Bob | bob@example.com | 555-123-4567 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 1  | John | john@example.com | 123-456-7890 |
| 5  | Mike | mike@example.com | 111-222-3333 |

#### OFFSET Clause

The OFFSET clause is used to skip a specified number of rows before starting to return rows. It is often used in conjunction with the LIMIT clause to implement pagination.

```sql
SELECT * FROM customers
ORDER BY name ASC
LIMIT 10 OFFSET 5;
```

This query retrieves the next 10 rows from the `customers` table, starting from the 6th row, sorted in ascending order by the `name` column.

**Example Table:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |
| 4  | Alice | alice@example.com | 901-234-5678 |
| 5  | Mike | mike@example.com | 111-222-3333 |
| 6  | David | david@example.com | 444-555-6666 |
| 7  | Emily | emily@example.com | 777-888-9999 |
| 8  | Frank | frank@example.com | 333-444-5555 |
| 9  | George | george@example.com | 666-777-8888 |
| 10 | Helen | helen@example.com | 999-000-1111 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 6  | David | david@example.com | 444-555-6666 |
| 7  | Emily | emily@example.com | 777-888-9999 |
| 8  | Frank | frank@example.com | 333-444-5555 |
| 9  | George | george@example.com | 666-777-8888 |
| 10 | Helen | helen@example.com | 999-000-1111 |

### Joining Tables

Joining tables is a way to combine rows from two or more tables based on a related column. There are several types of joins, including INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.

#### INNER JOIN

An INNER JOIN returns only the rows that have a match in both tables.

```sql
SELECT *
FROM customers
INNER JOIN orders
ON customers.id = orders.customer_id;
```

This query retrieves all rows from the `customers` table and the `orders` table where the `id` column in the `customers` table matches the `customer_id` column in the `orders` table.

**Example Tables:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| id | name | email | phone | id | customer_id | order_date | total |
|----|------|-------|-------|----|-------------|------------|-------|
| 1  | John | john@example.com | 123-456-7890 | 1  | 1           | 2022-01-01 | 100.00 |
| 1  | John | john@example.com | 123-456-7890 | 2  | 1           | 2022-01-15 | 200.00 |
| 2  | Jane | jane@example.com | 987-654-3210 | 3  | 2           | 2022-02-01 | 50.00 |

#### LEFT JOIN

A LEFT JOIN returns all rows from the left table and the matching rows from the right table. If there is no match, the result will contain NULL values.

```sql
SELECT *
FROM customers
LEFT JOIN orders
ON customers.id = orders.customer_id;
```

This query retrieves all rows from the `customers` table and the matching rows from the `orders` table. If there is no match, the result will contain NULL values.

**Example Tables:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| id | name | email | phone | id | customer_id | order_date | total |
|----|------|-------|-------|----|-------------|------------|-------|
| 1  | John | john@example.com | 123-456-7890 | 1  | 1           | 2022-01-01 | 100.00 |
| 1  | John | john@example.com | 123-456-7890 | 2  | 1           | 2022-01-15 | 200.00 |
| 2  | Jane | jane@example.com | 987-654-3210 | 3  | 2           | 2022-02-01 | 50.00 |
| 3  | Bob | bob@example.com | 555-123-4567 | NULL | NULL        | NULL      | NULL |

#### FULL OUTER JOIN

A FULL OUTER JOIN returns all rows from both tables, with NULL values in the columns where there are no matches.

```sql
SELECT *
FROM customers
FULL OUTER JOIN orders
ON customers.id = orders.customer_id;
```

This query retrieves all rows from the `customers` table and the `orders` table, with NULL values in the columns where there are no matches.

**Example Tables:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| id | name | email | phone | id | customer_id | order_date | total |
|----|------|-------|-------|----|-------------|------------|-------|
| 1  | John | john@example.com | 123-456-7890 | 1  | 1           | 2022-01-01 | 100.00 |
| 1  | John | john@example.com | 123-456-7890 | 2  | 1           | 2022-01-15 | 200.00 |
| 2  | Jane | jane@example.com | 987-654-3210 | 3  | 2           | 2022-02-01 | 50.00 |
| 3  | Bob | bob@example.com | 555-123-4567 | NULL | NULL        | NULL      | NULL |

### Subqueries

A subquery is a query nested inside another query. The subquery can be used to retrieve data that will be used in the main query.

```sql
SELECT *
FROM customers
WHERE id IN (
  SELECT customer_id
  FROM orders
  WHERE total > 100.00
);
```

This query retrieves all rows from the `customers` table where the `id` column is in the list of `customer_id` values retrieved from the `orders` table where the `total` column is greater than 100.00.

**Example Tables:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |

### Grouping and Aggregating Data

Grouping and aggregating data is used to combine rows of data into groups and perform calculations on each group.

```sql
SELECT customer_id, SUM(total) AS total_sales
FROM orders
GROUP BY customer_id;
```

This query retrieves the `customer_id` column and the sum of the `total` column for each group of rows with the same `customer_id` value.

**Example Table:**

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| customer_id | total_sales |
|-------------|-------------|
| 1           | 300.00      |
| 2           | 50.00       |

### Indexing and Optimizing Queries

Indexing and optimizing queries is used to improve the performance of queries by reducing the amount of data that needs to be scanned.

```sql
CREATE INDEX idx_customer_id ON orders (customer_id);
```

This query creates an index on the `customer_id` column of the `orders` table.

```sql
EXPLAIN SELECT * FROM orders WHERE customer_id = 1;
```

This query explains the execution plan of the query, including the indexes used.

**Example Table:**

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| id | select_type | table | type | possible_keys | key | key_len | ref | rows | Extra |
|----|-------------|-------|------|---------------|-----|---------|-----|------|-------|
| 1  | SIMPLE      | orders | ref  | idx_customer_id | idx_customer_id | 4     | const | 2    | NULL  |

### Database Design and Normalization

Database design and normalization is used to organize data in a database to minimize data redundancy and improve data integrity.

```sql
CREATE TABLE customers (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  phone VARCHAR(255)
);

CREATE TABLE orders (
  id INT PRIMARY KEY,
  customer_id INT,
  order_date DATE,
  total DECIMAL(10, 2),
  FOREIGN KEY (customer_id) REFERENCES customers (id)
);
```

This query creates two tables, `customers` and `orders`, with a foreign key constraint between the `customer_id` column of the `orders` table and the `id` column of the `customers` table.

**Example Tables:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

### Security and Access Control

Security and access control is used to control access to data in a database.

```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON customers TO 'user'@'localhost';
```

This query grants the `SELECT`, `INSERT`, `UPDATE`, and `DELETE` privileges on the `customers` table to the `user` user on the `localhost` host.

**Example Table:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

### Transaction Control

Transaction control is used to manage changes to data in a database.

```sql
START TRANSACTION;
INSERT INTO customers (name, email, phone) VALUES ('John Doe', 'john.doe@example.com', '123-456-7890');
COMMIT;
```

This query starts a transaction, inserts a new row into the `customers` table, and commits the transaction.

**Example Table:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |
| 4  | John Doe | john.doe@example.com | 123-456-7890 |

### Views

Views are virtual tables based on the result of a query. They are useful for simplifying complex queries, hiding sensitive data, and providing a layer of abstraction between the physical tables and the queries that access them.

```sql
CREATE VIEW customer_orders AS
SELECT customers.name, orders.order_date, orders.total
FROM customers
JOIN orders ON customers.id = orders.customer_id;
```

This query creates a view called `customer_orders` that retrieves the `name` column from the `customers` table, the `order_date` column from the `orders` table, and the `total` column from the `orders` table.

**Example Tables:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| name | order_date | total |
|------|------------|-------|
| John | 2022-01-01 | 100.00 |
| John | 2022-01-15 | 200.00 |
| Jane | 2022-02-01 | 50.00 |

### Stored Procedures

Stored procedures are reusable blocks of code that perform a specific task. They are useful for encapsulating complex logic, improving performance, and reducing code duplication.

```sql
DELIMITER //
CREATE PROCEDURE get_customer_orders(IN customer_id INT)
BEGIN
  SELECT orders.order_date, orders.total
  FROM orders
  WHERE orders.customer_id = customer_id;
END //
DELIMITER ;
```

This query creates a stored procedure called `get_customer_orders` that retrieves the `order_date` and `total` columns from the `orders` table for a given `customer_id`.

**Example Table:**

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| order_date | total |
|------------|-------|
| 2022-01-01 | 100.00 |
| 2022-01-15 | 200.00 |

### Triggers

Triggers are special types of stored procedures that are automatically executed in response to certain events, such as insert, update, or delete operations.

```sql
DELIMITER //
CREATE TRIGGER update_total
AFTER UPDATE ON orders
FOR EACH ROW
BEGIN
  UPDATE customers
  SET total = total + NEW.total
  WHERE id = NEW.customer_id;
END //
DELIMITER ;
```

This query creates a trigger called `update_total` that updates the `total` column in the `customers` table whenever an update operation is performed on the `orders` table.

**Example Tables:**

**customers**

| id | name | email | phone | total |
|----|------|-------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 | 0.00 |
| 2  | Jane | jane@example.com | 987-654-3210 | 0.00 |
| 3  | Bob | bob@example.com | 555-123-4567 | 0.00 |

**orders**

| id | customer_id | order_date | total |
|----|-------------|------------|-------|
| 1  | 1           | 2022-01-01 | 100.00 |
| 2  | 1           | 2022-01-15 | 200.00 |
| 3  | 2           | 2022-02-01 | 50.00 |

**Output:**

| id | name | email | phone | total |
|----|------|-------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 | 300.00 |
| 2  | Jane | jane@example.com | 987-654-3210 | 50.00 |
| 3  | Bob | bob@example.com | 555-123-4567 | 0.00 |

### Constraints

Constraints are rules that are applied to data in a table to ensure data integrity and consistency.

```sql
CREATE TABLE customers (
  id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE,
  phone VARCHAR(255) CHECK (LENGTH(phone) = 12)
);
```

This query creates a table called `customers` with several constraints, including a primary key constraint on the `id` column, a not null constraint on the `name` column, a unique constraint on the `email` column, and a check constraint on the `phone` column.

**Example Table:**

**customers**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |

**Output:**

| id | name | email | phone |
|----|------|-------|-------|
| 1  | John | john@example.com | 123-456-7890 |
| 2  | Jane | jane@example.com | 987-654-3210 |
| 3  | Bob | bob@example.com | 555-123-4567 |