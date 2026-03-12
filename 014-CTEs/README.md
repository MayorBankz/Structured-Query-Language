# SQL - CTEs (Common Table Expressions)
## DATE: 24-12-25
## TOOL - MySQL

---

### What is a CTE?
A CTE (Common Table Expression) is a temporary, named result set that you can use within a SQL query.
It helps make complex queries cleaner, more readable, and easier to maintain.

Think of a CTE as a temporary table that exists only while the query is running.
----

### Why Use CTEs?
CTEs are useful because they:

* Improve readability of complex queries

* Help break down large queries into smaller, logical steps

* Can be reused within the same query

* Make queries easier to debug and maintain

---

### BASIC SYNTAX
```sql
WITH cte_name AS (
        SELECT column1, column2
        FROM table_name
        WHERE condition
)
SELECT *
FROM cte_name;
```

### HOW IT WORKS
1. The CTE is created using the WITH keyboard
2. The query inside the parenthesis runs first
3. The result becomes a temporary table
4. The outer query uses that temporary result
---

### SIMPLE EXAMPLE 
* List customers who have made purchases above ₦500,000:

```sql
WITH HighValueCustomers AS (
    SELECT customer_id, total_amount
    FROM orders
    WHERE total_amount > 500000
)
SELECT *
FROM HighValueCustomers;
```
---
Explanation:

* The CTE HighValueCustomers stores customers with high purchase values

* The main query retrieves data from the CTE

---
### USING MULTIPLE CTEs
You can define more than one CTE in a single query:
```sql
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
```

---


### CTE vs Subquery
| CTE | Subquery |
| --- | -------- |
| Easier to read | Can be harder to read |
| Can be reused in the query | Usually used once |
| Named and structured | Not named |

---

### Key points to remember 
* CTEs start with the WITH keyword

* They are temporary and not stored in the database

* They exist only for the duration of the query

* Useful for complex logic and reports

---

### When to use a CTE 
Use a CTE when

* Your query is long or complex

* You want better readability

* You need to reuse query logic

---

### Types of CTEs
There are two main types of Common Table Expressions
1. Non-Recursive CTE
2. Recursive CTE

---

1. **Non-Recursive CTE**
Definition
A Non-Recursive CTE is a CTE that does not reference itselg.
It simply creates a temporary dataset that can be used in the main query.

These are commonly used to:
* Simpify complex queries
* Break down large SQL queries
* Improve readability
* Replace subqueries

---

### Example 1: Simple CTE 
Find customer with total sales greater than 1000.

```sql

WITH Customer_sales AS (
SELECT customerid,
sum(sales) as total_sales
FROM orders
GROUP BY customerid
)
SELECT *
FROM customer_sales
where total_sales > 1000;
```

### **Explanation**
1. The CTE customer_sales calculates total sales per customer
2. The main query filters customers whose sales exceed 1000

---

### Example 2: CTE with Join
Find the total orders for each customer

```sql
WITH order_count AS (
SELECT customerid,
        COUNT(orderid) as total_orders
FROM orders 
GROUP BY customerid
)
SELECT c.customerid,
        c.customername,
        o.total_orders
FROM customer as c
INNER JOIN order_count as o
        on c.customerid = o.customerid
```

### Explanation
1. The CTE calculates the number of orders per customer.
2. The result is joined with the customers table.

---

2. **Recursive CTE**

Definition

A Recursive CTE is a CTE that references itself.
It repeatedly executes until a specified condition is met.
Recursive CTEs are useful for working with hierarchical or tree-structured data, such as:
* Organizational charts
* Employee-manager relationships
* Category hierarchies
* Generating sequences

---

### **Structure of a Recursive CTE**
A recursive CTE has two parts:
1. **Anchor Query** - The starting part
2. **Recursive Query** - The part that references the CTE itself

---

### SYNTAX

```sql
WITH RECURSIVE cte_name AS (

    -- Anchor Query
    SELECT columns
    FROM table
    WHERE condition

    UNION ALL

    -- Recursive Query
    SELECT columns
    FROM table
    JOIN cte_name
        ON condition
)

SELECT *
FROM cte_name;
```

---

### Example 1 - Generate Numbers 1 to 5
```sql
WITH Recursive numbers AS (
SELECT 1 as num

UNION ALL

SELECT num + 1
FROM numbers
WHERE num < 5
)

SELECT *
FROM numbers;
```

### **RESULT**

| **num** |
| ------- |
| 1 |
| 2 |
| 3 |
| 4 |
| 5 |

### Explanation 
1. The anchor query starts with 1
2. The recursive query adds 1 each time
3. The process stops when num reaches 5

---

### Example 2: Employee Hierarchy
Assume we have this table:

| employeeid | name      | managerid |
| ---------- | --------- | --------- |
| 1          | CEO       | NULL      |
| 2          | Manager A | 1         |
| 3          | Manager B | 1         |
| 4          | Staff A   | 2         |

Query to retrieve hierarchy

```sql
WITH Recursive employee_hierarchy AS (
SELECT employeeid,
        name,
        managerid
FROM employees
WHERE managerid is NULL

UNION ALL

SELECT e.employeeid,
        e.name,
        e.managerid
FROM employees e
JOIN employee_hierarchy as eh
        ON e.managerid = eh.managerid
)
SELECT *
FROM employee_hierarchy;
```

### Expanation 
1. The anchor query finds the top manager(CEO)
2. The recursive query finds employees reporting to them.
3. The query continues until no more employees are found.

---

### **Advanatages of CTEs**
* Improves query readability
* Makes complex queries easier to manage
* Helps avoiding repeating subqueries
* Useful for hierarchical data analysis
* Can improve query organization
---

### Practical Example 

<img width="1060" height="402" alt="image" src="https://github.com/user-attachments/assets/42ed5049-b516-42b8-a4ba-154ee861625f" />
<img width="744" height="556" alt="image" src="https://github.com/user-attachments/assets/7457a69d-b77f-48bf-8f51-4a5c734df6eb" />

