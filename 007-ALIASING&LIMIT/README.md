# SQL - LIMIT & ALIASING
## Date - 13-12-2025
## TOOL - MySQL

## LIMIT IN SQL

What is LIMIT?

LIMIT is used to restrict the number of rows returned in a query result.

Why use LIMIT?

* To preview data

* To improve performance on large tables

* To return only top results (e.g., top 5 records)

### Example

SELECT *

FROM employees

LIMIT 5;

Explanation:
This query returns only the first 5 rows from the employees table.

## USING LIMIT WITH OFFSET

Example

SELECT *

FROM employees

LIMIT 5 OFFSET 10;

### Explanation:

OFFSET 10 skips the first 10 rows

LIMIT 5 returns the next 5 rows


## ALIASING IN SQL

What is Aliasing?

Aliasing allows you to rename a column or table temporarily for better readability.
The alias exists only for the duration of the query.

Why use Aliases?

* Makes column names easier to read

* Simplifies long or complex names

#### Example

SELECT salary AS monthly_salary

FROM employees;

Explanation:

The column salary will appear as monthly_salary in the result.

### Table Alias

SELECT e.name, e.department

FROM employees AS e;

Explanation:

* employees is shortened to e

* Makes the query cleaner and easier to write

### Alias Without AS

AS is optional in most SQL databases.

SELECT salary monthly_salary

FROM employees e;

## COMBINING ORDER BY with LIMIT in SQL

Why Use Them Together?

* ORDER BY sorts the result set

* LIMIT restricts the number of rows returned

👉 When combined, they allow you to get top or bottom results, such as:

* Top 5 highest salaries

* Latest 10 records

* Lowest 3 prices


### EXAMPLE

SELECT name, salary

FROM employees

ORDER BY salary DESC

LIMIT 5;

### Explanation:

* ORDER BY salary DESC → sorts salaries from highest to lowest

* LIMIT 5 → returns only the top 5 employees


## USING OFFSET WITH ORDER BY and LIMIT

SELECT *

FROM employees

ORDER BY employee_id

LIMIT 5 OFFSET 10;


### Explanation:

* Orders records by employee_id

* Skips the first 10 rows

* Returns the next 5 rows

### SUMMARY

| CLAUSE | PURPOSE |
| ------ | ------- |
| ORDER BY | Sorts the result set |
| ASC | sorts in ascending order (default) |
| DESC | sorts in descending order |
| LIMIT | Restricts number of rows returned |
| OFFSET | skips rows before returning results |

## Practical example 

### LIMIT

* SELECT all columns FROM table (employee_demographics) and LIMIT the rows to 3
  
<img width="865" height="493" alt="image" src="https://github.com/user-attachments/assets/e836a60d-151b-42b9-8550-1c38103c4335" />

### LIMIT & ORDER BY

* SELECT all columns FROM table (employee_demographics), arrange the age  ascending order (ORDER BY) and LIMIT the rows to 3
    
<img width="886" height="508" alt="image" src="https://github.com/user-attachments/assets/c74724de-7abf-40f8-809f-64baa01a178e" />

### LIMIT with OFFSET

* SELECT all columns FROM table (employee_demographics), arrange the age  ascending order (ORDER BY) and LIMIT the rows to 5 omit the first 3 rows (OFFSET)
  
<img width="861" height="515" alt="image" src="https://github.com/user-attachments/assets/658de26e-38a5-453b-b2dd-f7ed534c5a0d" />


### ALIASING 

* SELECT the column gender, aggregate with function AVG(age) aliasing as avg_age FROM table (employee_demographics) , then group by gender
<img width="851" height="445" alt="image" src="https://github.com/user-attachments/assets/5b7a8908-0969-4a30-9c7b-1331541ba063" />



