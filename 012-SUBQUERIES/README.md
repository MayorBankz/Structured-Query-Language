# SQL - SUBQUERIES
## DATE - 16-12-2025
## TOOL - MySQL

## Subqueries in SQL

A subquery is a query written inside another SQL query.
It is also called a nested query.

👉 The inner query runs first, and its result is then used by the outer query.
----
## Why Use Subqueries?
Subqueries help you:

* Filter data based on results from another query

* Compare values across tables

* Perform complex calculations in a simple way

* Create temporary result set

* Prepare data before joining table
---
### BASIC SYNTAX
```sql
SELECT column_name
FROM table_name
WHERE column_name operator (
    SELECT column_name
    FROM table_name
);
```
---
### SUBQUERY WITH DIFFERENT CLAUSES
1. Subquery in WHERE

Question: List customers who placed orders above the average order amount.
```sql
SELECT customer_name
FROM orders
WHERE order_amount > (
    SELECT AVG(order_amount)
    FROM orders
);
```
* The subquery finds the average order amount
* The outer query returns customers with orders greater than that average
---

2. Subquery with IN

Question: Find customers who have placed at least one order.

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
);
```
✔ The subquery returns customer IDs from the orders table
✔ The outer query matches them in the customers table

---

3. SUBQUERY WITH ANY
The ANY operator compares a value to any value returned by the subquery.

Condition becomes true if at least one comparison is true.

Syntax
```sql
SELECT column
FROM table
WHERE column OPERATOR ANY (subquery);
```

### Example
```sql
SELECT productid, sales
FROM orders
WHERE sales > ANY (
    SELECT sales
    FROM orders
    WHERE productid = 101
);
```
Explanation:

The condition is true if sales is greater than at least one value returned by the subquery.

---

4. Subquery with ALL
The ALL operator compares a value to all values returned by the subquery.

Condition becomes true only if it satisfies every value.

Syntax
```
SELECT column
FROM table
WHERE column OPERATOR ALL (subquery);
```

Example:
```sql
SELECT productid, sales
FROM orders
WHERE sales > ALL (
    SELECT sales
    FROM orders
    WHERE productid = 101
);
```
Explanation:

Sales must be greater than every value returned by the subquery.

---

5. Subquery with EXISTS
The EXISTS operator checks if the subquery returns any rows.
If the subquery returns at least one row, the condition is true.

Syntax
```sql
SELECT column
FROM table
WHERE EXISTS (subquery);
```

Example:
```sql
SELECT customerid
FROM customers c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customerid = c.customerid
);
```
Explanation:

Returns customers who have placed at least one order.

---
6. Subquery in SELECT Clause
A subquery can also appear inside the SELECT statement

Example:
```sql
SELECT 
customerid,
sales,
(SELECT AVG(sales) FROM orders) AS avg_sales
FROM orders;
```
Explanation
* The subquery calculates average sales

* The value appears in every row.

---

7. Subquery in FROM Clause (Derived Table)
A subquery can act as a temporary table.

Example
```sql
SELECT customerid, total_sales
FROM (
    SELECT customerid,
           SUM(sales) AS total_sales
    FROM orders
    GROUP BY customerid
) t
WHERE total_sales > 1000;
```
Explanation
Subquery calculates total sales per customer

Outer query filters customers with sales greater than 1000

--- 

8. Correlated vs Non-Correlated Subqueries
* Non-Correlated Subquery

Runs once and the result is used by the outer query.

Example
```sql
SELECT orderid, sales
FROM orders
WHERE sales > (
    SELECT AVG(sales)
    FROM orders
);
```
---
* Correlated Subquery
Runs once for every row in the outer query.
Example
```sql
SELECT customerid, orderid, sales
FROM orders o
WHERE sales > (
    SELECT AVG(sales)
    FROM orders
    WHERE customerid = o.customerid
);
```
Explanation
The subquery calculates average sales per customer.

The outer query returns orders above that customer's average.

---

### Types of Subqueries

1. Single-row subquery – returns one value
   Used with comparison operators: ( =, >, <, <=, =>, <>)

   Example:
```sql
   SELECT customerid, sales
FROM orders
WHERE sales > (
    SELECT AVG(sales)
    FROM orders
);
```
The subquery returns one value (average sales).

--- 

3. Multiple-row subquery – returns many values
4. Correlated subquery – depends on the outer query (advanced)


## Keypoints to Remeber

* Subqueries are enclosed in parentheses ()
* The inner query runs first
* They can be used in WHERE, SELECT, and FROM clauses.
* Useful for writing clean and readable SQL

## SUMMARY OF SUBQUERY OPERATORS
| OPERATOR | Description |
| -------- | ----------- |
| WHERE | Filters data using subquery result |
| IN | Matches values returned by subquery |
| ANY | True if condition matches any value |
| ALL | True if condition matches all values |
| EXISTS | True if subquery returns rows |


## Practical Example 

* SUBQUERIES - In this example, we are classifying our table (table_demographics) based on employee_id from another table(parks_departments) where the department ID is equals to 1.

<img width="907" height="600" alt="image" src="https://github.com/user-attachments/assets/84bff6f4-ca62-4adf-8bf8-6c3912f860d3" />

* SELECT the columns first_name and salary from the table (employee_salary), and calculate the average salary from the table employee_salary

<img width="978" height="472" alt="image" src="https://github.com/user-attachments/assets/ded8e24b-d2e7-4038-94f1-152413c4fe98" />

* Calculate the average maximum age of the subquery from employee_demographics
*  

<img width="1065" height="687" alt="image" src="https://github.com/user-attachments/assets/20cd4d46-eaac-4e24-9cc8-1962956def83" />


  


