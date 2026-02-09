# SQL-Learning-Journey
This repository contains my SQL learning and practice for Data Analytics.

SQL is a standard language for storing, manipulating, and retrieving data in databases. 
# What is SQL?
- SQL stands for Structured Query Language.

- SQL lets you access and manipulate databases.

- SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987.

# What Can SQL do?
- SQL can execute queries against a database
- SQL can retrieve data from a database
- SQL can insert records in a database
- SQL can update records in a database
- SQL can delete records from a database
- SQL can create new databases
- SQL can create new tables in a database
- SQL can create stored procedures in a database
- SQL can create views in a database
- SQL can set permissions on tables, procedures, and views

# What is RDBMS? 
RDBMS stands for Relational Database Management System.
RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.
The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries, and it consists of columns and rows.

# Some Basics 
We have a table named "Customer." Now in SQL Server 
```
SELECT * FROM Customer
```
Every table is broken up into smaller entities called fields. The fields in the Customers table consist of CustomerID, CustomerName, ContactName, Address, City, PostalCode and Country. A field is a column in a table that is designed to maintain specific information about every record in the table.
A record, also called a row, is each individual entry that exists in a table. For example, there are 91 records in the above Customers table. A record is a horizontal entity in a table.
A column is a vertical entity in a table that contains all information associated with a specific field in a table.
# SQL Statements
Most of the actions you need to perform on a database are done with SQL statements.
SQL statements consist of keywords that are easy to understand.
The following SQL statement returns all records from a table named "Customers":
```
SELECT * FROM Customers;
```
- SQL keywords are NOT case sensitive: select is the same as SELECT
- Semicolon(;) is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server.

# Some of The Most Important SQL Commands
- SELECT - extracts data from a database
- UPDATE - updates data in a database
- DELETE - deletes data from a database
- INSERT INTO - inserts new data into a database
- CREATE DATABASE - creates a new database
- ALTER DATABASE - modifies a database
- CREATE TABLE - creates a new table
- ALTER TABLE - modifies a table
- DROP TABLE - deletes a table
- CREATE INDEX - creates an index (search key)
- DROP INDEX - deletes an index

# SELECT Statement
The SELECT statement is used to select data from a database.
```
SELECT CustomerName, City FROM Customers;
```
- Syntax
  ```
  SELECT column1, column2, ...
  FROM table_name;
Here, column1, column2, ... are the field names of the table you want to select data from.
The table_name represents the name of the table you want to select data from.

Return all the columns from the Customers table:
```
SELECT * FROM Customers;
```
- The SQL SELECT DISTINCT Statement
  ```
  SELECT DISTINCT Country FROM Customers;
Select all the different countries from the "Customers" table:

- Count Distinct
  ```
  SELECT COUNT(DISTINCT Country) FROM Customers;
By using the DISTINCT keyword in a function called COUNT, we can return the number of different countries.

- Example
  ```
  SELECT Count(*) AS DistinctCountries
  FROM (SELECT DISTINCT Country FROM Customers);
# WHERE Clause
The WHERE clause is used to filter records. It is used to extract only those records that fulfill a specified condition.
For Example:
```
SELECT * FROM Customers
WHERE Country='Mexico';
```
Select all customers from Mexico.
- Syntax
  ```
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition;
# Text Fields vs. Numeric Fields
SQL requires single quotes around text values (most database systems will also allow double quotes).
However, numeric fields should not be enclosed in quotes. For Example 
```
SELECT * FROM Customers
WHERE CustomerID=1;
```
```
SELECT * FROM Customers
WHERE Country='Mexico';
```
# Operators in The WHERE Clause
You can use other operators than the = operator to filter the search. For Example:
```
SELECT * FROM Customers
WHERE CustomerID > 80;
```
The following operators can be used in the WHERE clause:

```
= Equal	
> Greater than	
< Less than	
>= Greater than or equal	
<=	Less than or equal	
<>	Not equal (Note: In some versions of SQL, this operator may be written as !=)
BETWEEN -	Between a certain range	
LIKE	Search for a pattern	
IN	To specify multiple possible values for a column
```
# The SQL ORDER BY
The ORDER BY keyword is used to sort the result set in ascending or descending order.
For Example:
```
SELECT * FROM Products
ORDER BY Price;
```
Sort the products by price.
- Syntax
  ```
  SELECT column1, column2, ...
  FROM table_name
  ORDER BY column1, column2, ... ASC/DESC;
- The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
- Order Alphabetically
  ```
  SELECT * FROM Products
  ORDER BY ProductName;
Sort the products alphabetically by ProductName.
- To sort the table reverse alphabetically, use the DESC keyword:
  ```
  SELECT * FROM Products
  ORDER BY ProductName DESC;
Sort the products by ProductName in reverse order.
- ORDER BY Several Columns

The following SQL statement selects all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName.
```
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```
- Using Both ASC and DESC

The following SQL statement selects all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column.
```
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```
# The SQL AND Operator



