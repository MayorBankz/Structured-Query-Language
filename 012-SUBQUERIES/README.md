# SQL - SUBQUERIES
## DATE - 16-12-2025
## TOOL - MySQL

## Subqueries in SQL

A subquery is a query written inside another SQL query.
It is also called a nested query.

👉 The inner query runs first, and its result is then used by the outer query.

## Why Use Subqueries?
Subqueries help you:

* Filter data based on results from another query

* Compare values across tables

* Perform complex calculations in a simple way

### BASIC SYNTAX

SELECT column_name
FROM table_name
WHERE column_name operator (
    SELECT column_name
    FROM table_name
);

### Example 1: Subquery in WHERE

Question: List customers who placed orders above the average order amount.

SELECT customer_name
FROM orders
WHERE order_amount > (
    SELECT AVG(order_amount)
    FROM orders
);

* The subquery finds the average order amount
* The outer query returns customers with orders greater than that average

### Example 2: Subquery with IN

Question: Find customers who have placed at least one order.

SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
);

✔ The subquery returns customer IDs from the orders table
✔ The outer query matches them in the customers table


### Types of Subqueries

1. Single-row subquery – returns one value
2. Multiple-row subquery – returns many values
3. Correlated subquery – depends on the outer query (advanced)


## Keypoints to Remeber

* Subqueries are enclosed in parentheses ()
* The inner query runs first
* They can be used in WHERE, SELECT, and FROM clauses.
* Useful for writing clean and readable SQL


## Practical Example 


