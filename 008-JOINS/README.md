# SQL - JOINS (INNER, OUTER, SELF etc.)
## Date - 14-12-2025
## Tool - MySQL

## WHAT IS A JOIN?

A JOIN in SQL is used to combine rows from two or more tables based on a related column between them.

### Why Joins are needed 

* Data is often stored in multiple tables

* JOINs help you retrieve meaningful information by linking those tables together

### COMMON TYPES OF SQL JOINS

1. INNER JOIN

   * Returns only matching records from both sides.

### SYNTAX

   <i>SELECT columns

FROM table1

INNER JOIN table2

ON table1.column = table2.column;</i>

Example 

<i>SELECT employees.name, departments.department_name

FROM employees

INNER JOIN departments

ON employees.department_id = departments.id;</i>

Only employees that belong to a department will be shown.

2. LEFT JOIN (LEFT OUTER JOIN)

   * Returns all records from the left table and matching records from the right table.
If there is no match, the result is NULL.

### SYNTAX

<i>SELECT columns

FROM table1

LEFT JOIN table2

ON table1.column = table2.column;</i>

### Example

<i>SELECT employees.name, departments.department_name

FROM employees

LEFT JOIN departments

ON employees.department_id = departments.id;</i>

* Shows all employees, even those without a department.

3. RIGHT JOIN (RIGHT OUTER JOIN)

   * Returns all records from the right table and matching records from the left table.
Unmatched values from the left table return NULL.

### Example

<i> SELECT employees.name, departments.department_name

FROM employees

RIGHT JOIN departments

ON employees.department_id = departments.id;</i>

* Shows all departments, even if no employee is assigned.

4. FULL JOIN

   * Returns all records from both tables.
If there is no match, the result contains NULL.

### Example

<i>SELECT employees.name, departments.department_name

FROM employees

FULL JOIN departments

ON employees.department_id = departments.id;</i>

5. SELF JOIN

   * A SELF JOIN is a join where a table is joined with itself. This is useful for hierarchical or recursive data, where a row in the table has a relationship with another row in the same table.

  ### SYNTAX

  <i>SELECT a.column1, b.column2

FROM table a

JOIN table b

ON a.column = b.column; </i>

### EXAMPLE

<i>SELECT e1.name AS Employee, e2.name AS Manager

FROM employees e1

JOIN employees e2

ON e1.manager_id = e2.id;</i>

### Explanation:

This query lists employees along with their managers, assuming manager_id in employees references the id of the manager in the same table.

6. JOINING MULTIPLE TABLES

   * You can join more than two tables by chaining multiple JOINs in a single query. This allows for more complex data relationships.

### SYNTAX

<i>SELECT columns

FROM table1

JOIN table2 ON table1.column = table2.column

JOIN table3 ON table2.column = table3.column;</i>

### Example

<i>SELECT employees.name, departments.department_name, locations.city

FROM employees

INNER JOIN departments ON employees.department_id = departments.id

INNER JOIN locations ON departments.location_id = locations.id;</i>

### Explanation:

This query joins three tables: employees, departments, and locations.

The result will show employees along with their department name and the location of that department.


## SUMMARY 

| JOIN TYPE | What it Returns |
| --------- | --------------- |
| INNER JOIN | Only rows with matching values in both tables |
| LEFT JOIN | All rows from the left table, matching rows from the right table |
| RIGHT JOIN | All rows from the right table, matching rows from the left table |
| FULL JOIN | All rows both tables, with NULLS where no match occurs |
| SELF JOIN | A table joined with itself |

### Practical Examples - MySQL

1. INNER JOIN

* joining the table employee_demographics and employee_salary using the INNER JOIN FUNCTION. only brings the rows with the same values.
  
<img width="1218" height="589" alt="image" src="https://github.com/user-attachments/assets/44a08344-8771-4804-8bdf-d47fe6eb130b" />

* Using aliasing
  
<img width="1213" height="532" alt="image" src="https://github.com/user-attachments/assets/78105086-5db4-4359-ae48-0ebd2bfc437e" />

* selecting columns on inner joins
  
<img width="841" height="525" alt="image" src="https://github.com/user-attachments/assets/fde31c83-d9d1-4c7f-9a20-85368a56b04c" />


2. LEFT OUTER JOIN

* Takes everything on the table (employee_demographics) and matches it with table (employee_salary). If there is no match it still brings out the rows
  
<img width="1218" height="556" alt="image" src="https://github.com/user-attachments/assets/6c482633-0a62-48c4-b4d0-1d9d09c4affb" />


3. RIGHT OUTER JOIN

* takes everything on the right table (employee_salary) and matches it with table (employee_demographics). If there is no match it still brings out the rows
  
<img width="1233" height="561" alt="image" src="https://github.com/user-attachments/assets/928fb0aa-eea5-47a6-a60b-2d12600faf08" />

4. SELF JOIN 

* Joining same tables (employee_salary) together
  
<img width="1385" height="524" alt="image" src="https://github.com/user-attachments/assets/97ecd566-11fa-464e-ad16-c7f1eebb8eeb" />

<img width="845" height="660" alt="image" src="https://github.com/user-attachments/assets/72cad584-cd5d-4335-9913-70ae7c37642e" />


5. JOINING MULTIPLE TABLES

<img width="1469" height="657" alt="image" src="https://github.com/user-attachments/assets/2d2ac176-4d07-4710-8724-20c56748b7eb" />










