# SQL - UNION
## Date - 15-12-205
## Tool - MySQL

## UNION IN SQL

### WHAT IS UNION?
UNION is an SQL operator used to combine the result sets of two or more SELECT queries into a single result.

* It removes duplicate rows by default

* Each SELECT statement must return:

    - The same number of columns

    - Compatible data types

    - Columns in the same order

### Basic Syntax

<i>SELECT column1, column2

FROM table1

UNION

SELECT column1, column2

FROM table2;</i>


### Example 

Assume we have two tables:

1. Customers_Nigeria
2. Customers_ghana

Query 

<i>SELECT name FROM Customers_Nigeria

UNION

SELECT name FROM Customers_Ghana;</i>

### RESULT - A single list of customer names from both tables, with no duplicates.

## UNION vs UNION ALL

| Feature | UNION | UNION ALL |
| ------- | ----- | --------- |
| Removes duplicates | Yes | No |
| Performance | Slower | Faster |

### Example

<i>SELECT name FROM Customers_Nigeria

UNION ALL

SELECT name FROM Customers_Ghana;</i>

### When to use UNION

* To merge similar data from multiple tables

* When tables have the same structure

* When duplicate records should be eliminated

### Important Notes
* Column names in the final result come from the first SELECT statement
* ORDEY BY can only be used at the end of the UNION query

<i>SELECT name FROM Customers_Nigeria

UNION

SELECT name FROM Customers_Ghana

ORDER BY name;</i>

## SUMMARY 

UNION helps you combine multiple query results into one clean dataset, making it useful for reporting and data analysis across similar tables.

## Practical Examples - MySQL

<img width="963" height="696" alt="image" src="https://github.com/user-attachments/assets/0fe231fa-5bce-4250-ada1-137a386fa02f" />

* UNION (DISTINCT)

<img width="932" height="675" alt="image" src="https://github.com/user-attachments/assets/1706f058-cd68-4b7b-96a7-7023f78db0b8" />

* UNION ALL

<img width="1066" height="873" alt="image" src="https://github.com/user-attachments/assets/1a0f8629-3412-453c-be53-d84fa91da3e8" />

<img width="937" height="563" alt="image" src="https://github.com/user-attachments/assets/582b7413-6b16-4ba0-9196-363be140576e" />

* UNION & ORDER BY FUNCTION

<img width="965" height="636" alt="image" src="https://github.com/user-attachments/assets/25a91cd7-3939-477d-927b-95fae3cef15c" />
