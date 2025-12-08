# SQL - SELECT, FROM & WHERE 
# DATE - 08-12-2025
# SOFTWARE - MySQL

## SELECT
The SELECT statement is used to specify the columns you want to retrieve from a database table.

Purpose

Choose which data (columns) you want to display.

Can be used with functions such as COUNT(), SUM(), AVG(), etc.

Example

SELECT <i>first_name, last_name</i>
FROM <i>employees;</i>

* This query retrieves only the first_name and last_name columns from the employees table.

## FROM
The FROM clause tells SQL which table to get the data from.

Purpose
Indicates the table or tables (in joins) you are selecting data from.

Example

SELECT *
FROM products;

* means select all columns from the products table.

## WHERE 
The WHERE clause is used to filter rows based on a condition.
It returns only the rows that meet the specified criteria.

Purpose 
* Filter results
* Apply conditions using:
* = (equal to)
*  | , <, >=, <=
*  AND, OR, NOT
*  LIKE (pattern matching)
*  BETWEEN
*  IN (multiple values)

SELECT *
FROM <i>employees</i<
WHERE department = <i>'IT';</i>

* This returns only employees who belong to the IT department.

## PUTTING THEM ALL TOGETHER
Full example query 

SELECT first_name, salary
FROM employees
WHERE salary > 50000;

Explanation
* SELECT first_name, salary → choose the columns to display
* FROM employees → get data from the employees table
* WHERE salary > 50000 → only return employees earning more than 50,000

## MULTIPLE CONDITIONS EXAMPLE
SELECT *
FROM <i></i>customers</i>
WHERE <i>country = 'USA' AND age > 25;</i>

Returns customers who:
* Live in the USA
* Are older than 25


