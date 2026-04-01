# TOPIC - INDEX
## DATE: 1-04-2026
## TOOL: MySQL

---

### **WHAT IS AN INDEX?**
An index is a database object that improves the speed of data retrieval from a table.
Think of it like a book index.
* Without index - Scan every page.
* With index - Jump directly to the page.

---

### **WHY USE INDEXES**?
Indexes help to:
* Speed up `SELECT` queries
* Improve filtering (`WHERE`, `JOIN`, `ORDER BY`)
* Reduce query execution time
⚠️ Trade-off:

* Slightly slower INSERT, UPDATE, DELETE
* Uses extra storage

---

### **TYPES OF INDEXES**

| Type            | Description                          | Example Use Case                |
| --------------- | ------------------------------------ | ------------------------------- |
| PRIMARY INDEX   | Automatically created on primary key | Unique row identification       |
| UNIQUE INDEX    | Ensures all values are unique        | Email, username                 |
| SINGLE-COLUMN   | Index on one column                  | Searching by `customerid`       |
| COMPOSITE INDEX | Index on multiple columns            | `(customerid, orderdate)`       |
| FULL-TEXT INDEX | Used for text searching              | Searching articles/descriptions |

---

### **BASIC SYNTAX**
Create Index
```sql
CREATE INDEX index_name
ON table_name (column_name);
```

Create Unique Index
```sql
CREATE UNIQUE INDEX index_name
ON table_name (column_name);
```

Create Composite Index
```sql
CREATE INDEX index_name
ON table_name (column1, column2);
```
Drop Index

```sql
DROP INDEX index_name ON table_name;
```
---

### **EXAMPLES**
1️⃣ Single Column Index
```sql
CREATE INDEX idx_customer
ON orders (customerid);
```

Use case: Faster filtering:
```sql
Use case: Faster filtering:
```

---

2️⃣ Composite Index
```sql
CREATE INDEX idx_customer_date
ON orders (customerid, orderdate);
```

Use case: Faster queries like:
```sql
SELECT * 
FROM orders 
WHERE customerid = 101 
AND orderdate = '2026-01-01';
```

---

3️⃣ Unique Index

```sql
CREATE UNIQUE INDEX idx_email
ON users (email);
```

Use case: Prevent duplicate emails

---

### **How Index Works (Simple Explanation)**

```sql
Scan all rows → slow ❌
```

With index:
```sql
Look up value → jump to row → fast ✅
```

---

### **When to Use Indexes**
✔️ Columns used in:

* `WHERE` conditions
* `JOIN` operations
* `ORDER BY` or `GROUP BY`

---

### **When NOT to Use Indexes**

❌ On columns with:

* Very few unique values (e.g., gender: M/F)
* Small tables (full scan is already fast)
* Frequently updated columns

---

### **Best Practices**
1. Index frequently queried columns
2. Use composite indexes for multi-column filters
3. Avoid too many indexes (affects performance)
4. Monitor performance using EXPLAIN

---

### **Using EXPLAIN (Performance Check)**
```sql
EXPLAIN SELECT * 
FROM orders 
WHERE customerid = 101;
```

👉 Helps you see if the index is being used

---

### **Key Takeaways**
* Index = faster reads, slower writes
* Use indexes for search-heavy queries
* Avoid unnecessary indexing
