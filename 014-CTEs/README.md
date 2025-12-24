# SQL - CTEs (Common Table Expressions)
## DATE: 24-12-25
## TOOL - MySQL

### What is a CTE?
A CTE (Common Table Expression) is a temporary, named result set that you can use within a SQL query.
It helps make complex queries cleaner, more readable, and easier to maintain.

Think of a CTE as a temporary table that exists only while the query is running.

### Why Use CTEs?
CTEs are useful because they:

* Improve readability of complex queries

* Help break down large queries into smaller, logical steps

* Can be reused within the same query

* Make queries easier to debug and maintain

### BASIC SYNTAX
WITH cte_name AS (
        SELECT column1, column2
        FROM table_name
        WHERE condition
)
SELECT *
FROM cte_name;

### SIMPLE EXAMPLE 
* List customers who have made purchases above ₦500,000:

WITH HighValueCustomers AS (
    SELECT customer_id, total_amount
    FROM orders
    WHERE total_amount > 500000
)
SELECT *
FROM HighValueCustomers;

Explanation:

* The CTE HighValueCustomers stores customers with high purchase values

* The main query retrieves data from the CTE

### USING MULTIPLE CTEs
You can define more than one CTE in a single query:

WITH Sales AS (
    SELECT order_id, amount
    FROM orders
),
HighSales AS (
    SELECT *
    FROM Sales
    WHERE amount > 500000
)
SELECT *
FROM HighSales;

### CTE vs Subquery
| CTE | Subquery |
| --- | -------- |
| Easier to read | Can be harder to read |
| Can be reused in the query | Usually used once |
| Named and structured | Not named |

### Key points to remember 
* CTEs start with the WITH keyword

* They are temporary and not stored in the database

* They exist only for the duration of the query

* Useful for complex logic and reports

### When to use a CTE 
Use a CTE when

* Your query is long or complex

* You want better readability

* You need to reuse query logic


### Practical Example 

<img width="1060" height="402" alt="image" src="https://github.com/user-attachments/assets/42ed5049-b516-42b8-a4ba-154ee861625f" />
<img width="744" height="556" alt="image" src="https://github.com/user-attachments/assets/7457a69d-b77f-48bf-8f51-4a5c734df6eb" />

