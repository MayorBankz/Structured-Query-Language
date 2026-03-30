# TOPIC : CTAS & TEMP TABLE
## DATE: 30-03-2026
## TOOL: MySQL

---

### WHAT IS CTAS?

CTAS means Create Table As Select.
👉 It is used to create a new table from an existing query result.

### SYNTAX
```sql
CREATE TABLE new_table As
SELECT column1, column2
FROM existing_table;
```

### Example

```sql
CREAYE TABLE high_value_customers As
SELECT customerid,
SUM(sales) as Total_sales
FROM Orders
GROUP BY customerid
HAVING SUM(sales) > 100;
```
---

### WHAT HAPPENS HERE?
* A new table called `high_valu_customers` is created
* It stores the result of the query
* The data is saved permanently (until you drop it)

 ---

 ### WHEN TO USE CTAS?
 * When you want to store query results permanently
 * When working with large datasets (faster than repeated queries)
 * For data transformation or backup

---

### WHAT IS A TEMPORARY TABLE

A temporary table is a table that exists only for a short time.
👉 It is usually deleted automatically when:
* The session ends or
* You manually drop it

---

### SYNTAX
Option 1: Create Temp Table + INSERT INTO

```sql
CREATE TEMP TABLE temp_sales (
    customerid INT,
    total_sales DECIMAL
);

INSERT INTO temp_sales
SELECT customerid, SUM(sales)
FROM orders
GROUP BY customerid;
```

---

Option 2: Create Temp Table Directly
```sql
CREATE TEMP TABLE temp_sales (
    customerid INT,
    total_sales DECIMAL
);

INSERT INTO temp_sales
SELECT customerid, SUM(sales)
FROM orders
GROUP BY customerid;
```
---

### Example Use Case

```sql
CREATE TEMP TABLE top_customers AS
SELECT customerid, SUM(sales) AS total_sales
FROM orders
GROUP BY customerid
HAVING SUM(sales) > 100;

SELECT * FROM top_customers;
```

---

🧠 Key Features of Temp Tables
* Exists temporarily
* Automatically deleted after session
* Useful for breaking complex queries into steps
* Improves readability and performance

---

### CTAS VS TEMPORARY TABLE

| Feature | CTAS | TEMPORARY TABLE |
| ------- | ---- | --------------- |
| Storage | Permanent | Temporary |
| Lifetime | Until dropped | Session-based |
| Use Case | Save results long-term | Intermediate calculations |
| Performance | Fast for large data | Fast for step-by-step logic |

---

⚠️ Important Notes

* Some databases use:
    * `CREATE TEMP TABLE` (PostgreSQL, MySQL)
    * `#temp_table` (SQL Server)
* CTAS may not allow constraints (like PRIMARY KEY) directly

---

🚀 Best Practice 
* Use CTAS - when you need final results saved
* Use Temp Tables - when solving complex queries step-by-step

---

🎯 Quick Summary

* CTAS = Create and store query result permanently
* Temp table = Store data temporarily for processing
