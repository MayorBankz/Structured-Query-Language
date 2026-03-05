# SQL VALUE WINDOW FUNCTION DOCUMENTATION
## TOOL: MySQL
## DATE: 05-03-2026

## OVERVIEW
Value window functions in SQL are used to access and calculate values across a set of rows (the “window”) without collapsing the result into a single row. 
These functions allow you to perform advanced analytics like ranking, comparisons, and aggregations while keeping row-level detail.

--- 

1. LAG()

Purpose: Access the value of a column from the previous row within the same partition.

### SYNTAX
```sql
LAG(column, offset, default_value) OVER (
    [PARTITION BY partition_column]
    ORDER BY order_column
)
```

* `column` → the column whose previous value you want

* `offset` → how many rows back (default = 1)

* `default_value` → value if there’s no previous row

* `PARTITION BY` → divides rows into groups

* `ORDER BY` → determines row order within each partition

### EXAMPLE
```sql
SELECT 
    customerid,
    orderdate,
    sales,
    LAG(sales) OVER(PARTITION BY customerid ORDER BY orderdate) AS prev_sales
FROM salesdb.orders;
```

Explanation: Retrieves the previous order's sales for each customer.

---

2. LEAD()

Purpose: Access the value of a column from the next row within the same partition.
### SYNTAX
```sql
LEAD(column, offset, default_value) OVER (
    [PARTITION BY partition_column]
    ORDER BY order_column
)
```
Example:
```sql
SELECT 
    customerid,
    orderdate,
    sales,
    LEAD(orderdate) OVER(PARTITION BY customerid ORDER BY orderdate) AS next_order
FROM salesdb.orders;
```
Explanation: Retrieves the next order date for each customer.

---

3. FIRST_VALUE()
Purpose: Returns the first value in the window according to the specified order.
### SYNTAX
```sql
FIRST_VALUE(column) OVER (
    [PARTITION BY partition_column]
    ORDER BY order_column
    [ROWS BETWEEN frame_specification]
)
```

### EXAMPLE 
```sql
SELECT 
    productid,
    sales,
    FIRST_VALUE(sales) OVER(PARTITION BY productid ORDER BY sales) AS lowest_sale
FROM salesdb.orders;
```
Explanation: Retrieves the lowest sale for each product.

4. LAST_VALUE()
Purpose: Returns the last value in the window according to the specified order.

Important: You usually need to adjust the frame; otherwise, it may return the current row value instead of the true last value.

### SYNTAX
```sql
LAST_VALUE(column) OVER (
    [PARTITION BY partition_column]
    ORDER BY order_column
    ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING
)
```

### EXAMPLE
```sql
SELECT 
    productid,
    sales,
    LAST_VALUE(sales) OVER(PARTITION BY productid ORDER BY sales
        ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) AS highest_sale
FROM salesdb.orders;
```

Explanation: Retrieves the highest sale for each product.

---

5. MIN() and MAX() as Window Functions
Purpose: Get the minimum or maximum value within a window without collapsing rows.

### SYNTAX 
```sql
MIN(column) OVER ([PARTITION BY partition_column])
MAX(column) OVER ([PARTITION BY partition_column])
```

### EXAMPLE 
```sql
SELECT 
    productid,
    sales,
    MIN(sales) OVER(PARTITION BY productid) AS min_sale,
    MAX(sales) OVER(PARTITION BY productid) AS max_sale
FROM salesdb.orders;
```

Explanation: Retrieves the lowest and highest sales per product.

---

6. RANK()

Purpose: Assigns a rank to each row within a partition based on the order of a column. Ties get the same rank, with gaps.

Syntax:

```sql
RANK() OVER (
    [PARTITION BY partition_column]
    ORDER BY order_column [ASC|DESC]
)
```

### EXAMPLE
```sql
SELECT 
    customerid,
    ROUND(AVG(DaysBetweenOrders),0) AS avg_days,
    RANK() OVER(ORDER BY AVG(DaysBetweenOrders)) AS loyalty_rank
FROM customer_orders
GROUP BY customerid;
```
Explanation: Ranks customers based on their average days between orders. Smaller averages = more loyal.

---

7. DENSE_RANK()
Purpose: Like RANK(), but without gaps when multiple rows tie.

### EXAMPLE 
```sql
SELECT 
    customerid,
    sales,
    DENSE_RANK() OVER(PARTITION BY productid ORDER BY sales DESC) AS rank_per_product
FROM salesdb.orders;
```

Explanation: Assigns consecutive ranks to sales per product, even if values tie.

---

8. ROW_NUMBER()

Purpose: Assigns a unique sequential number to each row in the window.

### Example:
```sql
SELECT 
    customerid,
    orderdate,
    ROW_NUMBER() OVER(PARTITION BY customerid ORDER BY orderdate) AS row_num
FROM salesdb.orders;
```

Explanation: Useful for identifying first or last orders, duplicates, or sampling.

---

9. Framing Options (ROWS BETWEEN …)
Framing determines which rows the window function considers. Common examples:

* ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW → all rows from the start of partition up to current row

* ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING → current row to the end of the partition

### Example:
```sql
LAST_VALUE(sales) OVER(
    PARTITION BY productid
    ORDER BY sales
    ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING
)
```

Explanation: Ensures `LAST_VALUE()` captures the true last value.

--- 

✅ Key Takeaways

1. Value window functions operate row-by-row but can see other rows in the same partition.

2. Partitioning separates the data into groups for independent calculations.

3. Ordering controls the sequence of rows for functions like `LAG()`, `LEAD()`, `FIRST_VALUE()`, `LAST_VALUE()`.

4. Ranking functions `(RANK()`, `DENSE_RANK()`, `ROW_NUMBER())` assign positions to rows based on order.

5. Aggregation window functions `(MIN()`, `MAX()`, `AVG())` calculate metrics without collapsing rows.
