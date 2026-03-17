## TOPIC - VIEWS IN SQL
## TOOL - MySQL
## DATE - 17-03-2026
---

### **📌 WHAT IS VIEW?**

A view in SQL is a **virtual table** created from a query.

👉 Instead of storing data, a view stores a SQL query, and every time you use it, the database runs that query.

Think of it like:
  A saved query you can reuse like a table.

---

### **🎯 Why Use Views?**
Views help you:
* Simplify complex queries
* Improve security
* Reuse logic
* Make your SQL cleaner

---

### **⚙️ Basic Syntax**
```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

---

### **✅ Example 1: Simple View**

```sql
CREATE VIEW high_sales_orders AS
SELECT orderid, customerid, sales
FROM orders
WHERE sales > 100;
```
👉 Now you can use it like a table:
---

```sql
SELECT * FROM high_sales_orders;
```

---

### **✅ Example 2: View with Join**
```sql
CREATE VIEW customer_sales AS
SELECT c.customerid,
       c.customername,
       SUM(o.sales) AS total_sales
FROM customers c
JOIN orders o
ON c.customerid = o.customerid
GROUP BY c.customerid, c.customername;
```

---

### **🔄 Updating a View**

```sql
CREATE OR REPLACE VIEW view_name AS
SELECT ...
```
---

### **❌ Deleting a View**

---

### **🚀 Advantages of Views**

1. Simplicity - Hide complex logic (joins, aggregations)
2. Reusability - Write once, use many times
3. Security - Restrict access to certain columns or rows
4. Consistency - Everyone uses the same logic(no duplicate queries)

---
### **💼 Common Use Cases**
✅ 1. Data Filtering
Show only relevant data
```sql
CREATE VIEW active_customers AS
SELECT *
FROM customers
WHERE status = 'Active';
```
---

✅ 2. Data Aggregation
Pre-calculate totals
```sql
CREATE VIEW customer_totals AS
SELECT customerid,
       SUM(sales) AS total_sales
FROM orders
GROUP BY customerid;
```

---

✅ 3. Security Layer

Hide sensitive data

```sql
CREATE VIEW public_customer_data AS
SELECT customerid, customername
FROM customers;
```

---

✅ 4. Reporting & Dashboards
Used heavily in BI tools (Power BI, Tableau)

---

### **⚠️ Important Things to Note**
🔶1. Views don't store data
* They run the query every time
* Can be slower if query is complex

---
🔶2. Not always updateable
You cannot update a view if it contains:
* `GROUP BY`
* `JOIN`
* `DISTINCT`
* Aggregations (`SUM`, `AVG`, etc.)

---

♦️3. Performance matters
* Complex view = slower queries
* Use indexes on underlying tables

---

♦️4. Nested views can be confusing
* Avoid stacking views on views too much

---

♦️5. Use Meaningful Names
Bad ❌: view1
Good ✅: customer_total_sales

---

### **🧠 Pro Tips**
✔ Use views to simplify repeated logic
✔ Great for dashboards and reporting
✔ Combine with CTEs for clean queries
✔ Use materialized views (if supported) for better performance

---

### **Views vs Table**

| **Feature** | **View** | **Table** |
| ------ | ------ | ----- |
| Stores data | No | Yes |
| Stores query | Yes | No |
| Performance | slower(sometimes) | Faster |
| Use caes | Logic & abstraction | Data storage |

---

### **Conclusion**

Views are powerful for 
* Simplifying SQL
* Reusing logic
* Securing data



