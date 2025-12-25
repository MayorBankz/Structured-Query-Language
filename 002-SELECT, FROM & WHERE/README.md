# SQL - SELECT, FROM & WHERE 
# DATE - 08-12-2025
# SOFTWARE - MySQL

## SELECT
The SELECT statement is used to specify the columns you want to retrieve from a database table.

Purpose

Choose which data (columns) you want to display.

Can be used with functions such as COUNT(), SUM(), AVG(), etc.

Example

```sql
    SELECT <i>first_name, last_name</i>
    FROM <i>employees;</i>
```

* This query retrieves only the first_name and last_name columns from the employees table.

## FROM
The FROM clause tells SQL which table to get the data from.

Purpose
Indicates the table or tables (in joins) you are selecting data from.

Example
```sql 
SELECT *
FROM products;
```
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

```sql
SELECT *
FROM <i>employees</i>
WHERE department = <i>'IT';</i>
```

* This returns only employees who belong to the IT department.

## PUTTING THEM ALL TOGETHER
Full example query 

```sql
SELECT first_name, salary
FROM employees
WHERE salary > 50000;
```

Explanation

```sql
* SELECT first_name, salary → choose the columns to display
* FROM employees → get data from the employees table
* WHERE salary > 50000 → only return employees earning more than 50,000
```

## MULTIPLE CONDITIONS EXAMPLE

```sql
SELECT *
FROM <i></i>customers</i>
WHERE <i>country = 'USA' AND age > 25;</i>
```

Returns customers who:
* Live in the USA
* Are older than 25


## Practical Example - MySQL

A database parks and recreation is used in this session. It consists of the following tables;
* employee_demographics
* employee_salary
* parks_departments

## Table 1 - employee_demographics

<img width="910" height="511" alt="image" src="https://github.com/user-attachments/assets/66a54abd-ee7a-4e33-b0ab-ef010395390c" />

## Table 2 - employee_salary

<img width="962" height="546" alt="image" src="https://github.com/user-attachments/assets/428a56b2-68a3-4c38-9970-6c3ae478c22c" />


### Task 1
Using the "SELECT & FROM" query to view the entire table
* SELECT all columns (*) FROM employee_demographics; 

<img width="1007" height="691" alt="image" src="https://github.com/user-attachments/assets/f9ef3098-1678-494d-9f3f-1d9a42e58a49" />


* SELECT all columns (*) FROM parks_and_recreation.employee_demographics;
* The query "parks_and_recreation.employee_demographics" means from table (employee_demographics) from database (parks_and_recreation).
  
<img width="897" height="564" alt="image" src="https://github.com/user-attachments/assets/26bf491e-2428-4086-9766-d65f756e5fe1" />

* SELECT the columns first_name, last_name, birth_date, age from the table (employee_demographics) from the database (parks_and_recreation)
  
<img width="994" height="520" alt="image" src="https://github.com/user-attachments/assets/9e6dabc2-0a41-4a37-a7fd-7c360b6f705d" />



* SELECT the column first_name from the table (employee_demographics) from the database (parks_and_recreation), where the row for column first_name is 'Leslie"
<img width="855" height="405" alt="image" src="https://github.com/user-attachments/assets/46531fc9-2d3c-404c-a18f-3c725be6c26e" />

* SELECT all columns from the table (employee_salary) from database (parks_and_recreation) WHERE salary is greater than or equal to (>=) 50000.

<img width="1109" height="512" alt="image" src="https://github.com/user-attachments/assets/9872ba85-1dd5-4c31-842b-167d0e08d14f" />


* SELECT all columns from table (employee_demographics) from database (parks_and_recreation), WHERE gender is not equal to (!=) female.
  
<img width="1014" height="475" alt="image" src="https://github.com/user-attachments/assets/cdf17426-3d25-44c2-9a48-958d58df127c" />












