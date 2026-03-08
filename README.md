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
The WHERE clause can contain one or many AND operators.
The AND operator is used to filter records based on more than one condition, like if you want to return all customers from Spain that start with the letter 'G'.
```
SELECT *
FROM Customers
WHERE Country = 'Spain' AND CustomerName LIKE 'G%';
```
Select all customers from Spain that start with the letter 'G'.
- Syntax
  ```
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition1 AND condition2 AND condition3 ...;
# AND vs OR
- The AND operator displays a record if all the conditions are TRUE.
- The OR operator displays a record if any of the conditions are TRUE.
- Example
The following SQL statement selects all fields from Customers where Country is "Brazil" AND City is "Rio de Janeiro" AND CustomerID is higher than 50.
```
SELECT * FROM Customers
WHERE Country = 'Brazil'
AND City = 'Rio de Janeiro'
AND CustomerID > 50;
```
- Combining AND and OR
You can combine the AND and OR operators.
The following SQL statement selects all customers from Spain that starts with a "G" or an "R".
Make sure you use parenthesis to get the correct result.
```
SELECT * FROM Customers
WHERE Country = 'Spain' AND (CustomerName LIKE 'G%' OR CustomerName LIKE 'R%');
```
Select all Spanish customers that starts with either "G" or "R".

# The SQL OR Operator
The WHERE clause can contain one or more OR operators.
The OR operator is used to filter records based on more than one condition, like if you want to return all customers from Germany but also those from Spain.
```
SELECT *
FROM Customers
WHERE Country = 'Germany' OR Country = 'Spain';
```
Select all customers from Germany or Spain.
- Syntax
  ```
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition1 OR condition2 OR condition3 ...;
- OR vs AND
The OR operator displays a record if any of the conditions are TRUE.

The AND operator displays a record if all the conditions are TRUE.
- At Least One Condition Must Be True
- 
  The following SQL statement selects all fields from Customers where either City is "Berlin", CustomerName starts with the letter "G" or Country is "Norway".
  ```
  SELECT * FROM Customers
  WHERE City = 'Berlin' OR CustomerName LIKE 'G%' OR Country = 'Norway';

- Combining AND and OR

You can combine the AND and OR operators.
The following SQL statement selects all customers from Spain that starts with a "G" or an "R".
Make sure you use parenthesis to get the correct result.
```
SELECT * FROM Customers
WHERE Country = 'Spain' AND (CustomerName LIKE 'G%' OR CustomerName LIKE 'R%');
```
Select all Spanish customers that starts with either "G" or "R".

# The NOT Operator

The NOT operator is used in combination with other operators to give the opposite result, also called the negative result.
In the select statement below we want to return all customers that are NOT from Spain.
```
SELECT * FROM Customers
WHERE NOT Country = 'Spain';
```
Select only the customers that are NOT from Spain.

In the example above, the NOT operator is used in combination with the = operator, but it can be used in combination with other comparison and/or logical operators. See examples below.

- Syntax
  ```
  SELECT column1, column2, ...
  FROM table_name
  WHERE NOT condition;

- NOT LIKE
  ```
  SELECT * FROM Customers
  WHERE CustomerName NOT LIKE 'A%';
Select customers that does not start with the letter 'A'.

- NOT BETWEEN
  ```
  SELECT * FROM Customers
  WHERE CustomerID NOT BETWEEN 10 AND 60;
Select customers with a customerID not between 10 and 60.
- NOT IN
  ```
  SELECT * FROM Customers
  WHERE City NOT IN ('Paris', 'London');
  
Select customers that are not from Paris or London.
- NOT Greater Than
   ```
  SELECT * FROM Customers
  WHERE NOT CustomerID > 50;
Select customers with a CustomerId not greater than 50.

- NOT Less Than
  ```
  SELECT * FROM Customers
  WHERE NOT CustomerId < 50;
Select customers with a CustomerID not less than 50.

# INSERT INTO Statement
The INSERT INTO statement is used to insert new records in a table.
- Syntax
  ```
  INSERT INTO table_name (column1, column2, column3, ...)
  VALUES (value1, value2, value3, ...);
  ```
  ```
  INSERT INTO table_name
  VALUES (value1, value2, value3, ...);

# NULL Values
- What is a NULL Value?

If a field in a table is optional, it is possible to insert or update a record without adding any value to this field. This way, the field will be saved with a NULL value.

A NULL value represents an unknown, missing, or inapplicable data in a database field. It is not a value itself, but a placeholder to indicate the absence of data.
- Note: A NULL value is different from zero (0) or an empty string (''). A field with a NULL value is one that has been left blank upon record creation.

- IS NULL Syntax
  ```
  SELECT column_names
  FROM table_name
  WHERE column_name IS NULL;
- IS NOT NULL Syntax
  ```
  SELECT column_names
  FROM table_name
  WHERE column_name IS NOT NULL;
# The SQL UPDATE Statement
The UPDATE statement is used to update or modify one or more records in a table.
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
- Note: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, all records in the table will be updated!

# The SQL DELETE Statement
The DELETE statement is used to delete existing records in a table.
```
DELETE FROM table_name WHERE condition;
```
- Note: Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted. If you omit the WHERE clause, all records in the table will be deleted!
- Delete All Records
  ```
  DELETE FROM table_name;
- Delete a Table
  ```
  DROP TABLE table_name;

# The SQL SELECT TOP Clause 

The SELECT TOP clause is used to limit the number of records to return.

The SELECT TOP clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.

The following SQL selects only the first 3 records of the "Customers" table:

```
SELECT TOP 3 * FROM Customers;
```
- Note: Not all database systems support the SELECT TOP clause. MySQL supports the LIMIT clause to select a limited number of records, while Oracle uses FETCH FIRST n ROWS ONLY.

- Syntax

```
1) Syntax for SQL Server / MS Access
SELECT TOP num ber|percent column_name(s)
FROM table_name
WHERE condition;

2) Syntax for MySQL
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;

3) Syntax for Oracle 12+
SELECT column_name(s)
FROM table_name
ORDER BY column_name(s)
FETCH FIRST number ROWS ONLY;
```

# SQL Aggregate Functions
An aggregate function is a function that performs a calculation on a set of values, and returns a single value.
Aggregate functions are often used with the ``GROUP BY`` clause of the ```SELECT``` statement. The ```GROUP BY``` clause splits the result-set into groups of values and the aggregate function can be used to return a single value for each group.

The most commonly used SQL aggregate functions are:
- MIN() - returns the smallest value of a column
- MAX() - returns the largest value of a column
- COUNT() - returns the number of rows in a set
- SUM() - returns the sum of a numerical column
- AVG() - returns the average value of a numerical column

Aggregate functions ignore null values (except for COUNT(*)).


The behavior of COUNT() depends on the argument used within the parentheses:
- ```COUNT(*)``` - Counts the total number of rows in a table (including NULL values).
- ```COUNT(columnname)``` - Counts all non-null values in the column.
- ```COUNT(DISTINCT columnname)``` - Counts only the unique, non-null values in the column.


# SQL LIKE Operator 

The  ```LIKE``` operator is used in a ```WHERE``` clause to search for a specified pattern within a column's text data.

There are two wildcards often used in conjunction with the LIKE operator:
- A percent sign % - represents zero, one, or multiple characters
- A underscore sign _ - represents a single character
```
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```
# SQL Wildcard Characters
A wildcard character is used to substitute one or more characters in a string.

Wildcard characters are used with the ```LIKE``` operator. The ```LIKE``` operator is used in a ```WHERE``` clause to search for a specified pattern in a column.
For Example:
```
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```

# The SQL IN Operator
The ```IN``` operator is used in the WHERE clause to check if a specified column's value matches any value within a provided list.

The IN operator functions as a shorthand for multiple OR conditions, making queries shorter and more readable.

The following SQL uses the IN operator to select all customers from Germany, France, or UK:
```
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');
```
- Syntax
  ```
  SELECT column_name(s)
  FROM table_name
  WHERE column_name IN (value1, value2, ...);

# The NOT IN Operator
By using the NOT IN operator, you return all records that are NOT any of the values in the list. For example 
```
SELECT * FROM Customers
WHERE Country NOT IN ('Germany', 'France', 'UK');
```
Return all customers that are NOT from 'Germany', 'France', or 'UK'.

# IN (SELECT)
You can also use IN with a subquery in the WHERE clause.

With a subquery you can return all records from the main query that are present in the result of the subquery.

The following SQL returns all customers who also have an order in the "Orders" table:

```
SELECT * FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Orders);
```

# NOT IN (SELECT) 
The result in the example above returned 74 records, that means that there are 17 customers that haven't placed any orders.

Let us check if that is correct, by using the NOT IN operator.

The following SQL returns all customers who NOT have an order in the "Orders" table
```
SELECT * FROM Customers
WHERE CustomerID NOT IN (SELECT CustomerID FROM Orders);
```

















