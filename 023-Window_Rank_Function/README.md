# TOPIC: WINDOW RANK FUNCTION
## TOOL: MySQL
## DATE: 03-03-26

--- 

📌 WHAT IS RANK()?
The RANK() function is a window function that assigns a rank(position number) to each row based on a specific order.

--- 

It is commonly used to:
* Rank sales
* Rank scores
* Find top customers
* Compare value within groups

---
### BASIC SYNTAX
```sql
RANK() OVER (
    [PARTITION BY column_name]
    ORDER BY column_name [ASC | DESC]
)
```

---

### HOW IT WORKS
* `RANK()` - Assigns ranking number
* `OVER()` - Defines how the ranking should be applied
* `ORDER BY()` - Determines the ranking order
* `PARTITION BY`(optional) - Divides data into groups before ranking.

---

### Example 1: Rank orders by sales (Highest to Lowest)
```sql
SELECT 
    orderid,
    orderdate,
    sales,
    RANK() OVER (ORDER BY sales DESC) AS sales_rank
FROM orders;
```

### WHAT THIS DOES 
* Orders are ranked from highest sales to lowest.
* The highest sales gets rank 1.

---

### Example 2: Rank Sales Per Customer

```sql
SELECT 
    customer_id,
    orderid,
    sales,
    RANK() OVER (PARTITION BY customer_id ORDER BY sales DESC) AS customer_sales_rank
FROM orders;
```

### WHAT THIS DOES 
* Each customer's orders are ranked separately.
* Ranking restarts for every customer.

---

⚠️ Important: How RANK() Handles Ties
If two rows have the same value:
Example sales:

| Sales | Rank |
| ----- | ---- |
| 500 | 1 |
| 400 | 2 |
| 400 | 2 |
| 300 | 4 |

### Notice:
* Both '400s' get rank 2
* Rank 3 is skipped.
This is called **"ranking with gaps"**

---

🔄 Difference Between RANK() and DENSE_RANK()

| Function | Skip Numbers |
| -------- | ------------ |
| `RANK()` | ✅ Yes |
| `DENSE_RANK` | ❌ NO |

---

🎯 When to Use RANK()
Use RANK() when:
* You want competition-style ranking
* You want ties to share the same rank
* Skipping number after ties is acceptable

---

## WINDOW RANKING FUNCTIONS
Window ranking functions assign position numbers or percentages to rows based on a defined order.

They are mainly divided into:

* Integer-based ranking

* Percentage-based ranking

---

1️⃣ Integer-Based Ranking Functions 

🔹 `ROW_NUMBER() ` - Assigns a unique number to each row.
```sql
ROW_NUMBER() OVER (ORDER BY column_name)
```
✅ Key Rule:
* No ties.

* Even if values are the same, each row gets a different number.

📌 Use Cases:

* Assign unique IDs

* Pagination

* Removing duplicates (keep row_number = 1)
---

🔹 `RANK()` - Assigns ranking with gaps when there are ties.
```sql
RANK() OVER (ORDER BY column_name DESC)
```
✅ Tie Rule:

If two rows tie:

* They get the same rank

* The next rank is skipped

Example: 
| Sales | Rank |
| ----- | ---- |
| 500 | 1 |
| 400 | 2 |
| 400 | 2 |
| 300 | 4 |

---

🔹 `DENSE_RANK()` - Assigns ranking without gaps.
```sql
DENSE_RANK() OVER (ORDER BY column_name DESC)
```
✅ Tie Rule:

If two rows tie:

They get the same rank

No number is skipped

Example:

| Sales | Dense Rank |
| ----- | ---------- |
| 500 | 1 |
| 400 | 2 |
| 400 | 2 |
| 300 | 3 |

---

🔹 `NTILE(n)` - Divides rows into n equal groups (buckets).

```sql
NTILE(4) OVER (ORDER BY sales DESC)
```
📌 Use Cases:
* Data Segmentation
* Quartiles (4 groups)
* Deciles (10 groups)
* Equal workload distribution
* Balanced data processing
If you use `NTILE(4)`, rows are divided into 4 almost equal groups.

---

2️⃣ Percentage-Based Ranking Functions
These return values between 0 and 1.

---

🔹 PERCENT_RANK() - Shows the relative rank of a row.

### FORMULA 
(rank - 1) / (total_rows - 1)

✅ Key Points:
* First row = 0
* Last row = 1
* Based on `RANK()` logic (has gaps if ties exist)

---

🔹 `CUME_DIST()` - Shows cumulative distribution.
Formula
number_of_rows_with_value_less_or_equal / total_rows

✅ Key Points:
* Value between 0 and 1
* Always greater than 0
* Based on cumulative position
* Does NOT skip based on rank gaps
---

📌 Tie Rules Summary

| **Function** | **Ties Share Rank** | **Skip numbers** |
| ----------- | ---------------- | ------------- |
| ROW_NUMBER() | ❌ No | ❌ No |
| RANK() | ✅ Yes | ✅ Yes |
| DENSE_RANK() | ✅ Yes | ❌ No |
| NTILE() | ❌ No | ❌ No |
| PERCENT_RANK() | ✅ Yes (uses RANK logic) | ✅ Yes |
| CUME_DIST() | ✅ Yes (cumulative) | ❌ No |

---

🎯 Practical Use Cases
1️⃣ Top-N Analysis
Find top 5 highest sales:
```sql
SELECT *
FROM (
    SELECT *,
           RANK() OVER (ORDER BY sales DESC) AS sales_rank
    FROM orders
) t
WHERE sales_rank <= 5;
```

---

2️⃣ Bottom-N Analysis
Find lowest 3 sales:
```sql
ORDER BY sales ASC| 
```
---

3️⃣ Assign Unique IDs / Pagination

```sql
ROW_NUMBER() OVER (ORDER BY orderdate)
```

Pagination example:
```sql
WHERE row_num BETWEEN 11 AND 20
```
---

4️⃣ Identify Duplicates
```sql
SELECT *
FROM (
    SELECT *,
           ROW_NUMBER() OVER (PARTITION BY email ORDER BY id) AS rn
    FROM customers
) t
WHERE rn > 1;
```

---

5️⃣ Data Segmentation (NTILE)
Divide customers into 4 groups:
```sql
NTILE(4) OVER (ORDER BY total_sales DESC)
```
---

Useful for:

* Customer tiers

* Performance bands

* Balanced task allocation
---

🚀 Quick Summary

* Integer ranking → Position numbers

* Percentage ranking → Relative position (0 to 1)

* `ROW_NUMBER()` → Unique numbering

* `RANK()` → Competition ranking (with gaps)

* `DENSE_RANK()` → Ranking without gaps

* `NTILE()` → Equal grouping

* `PERCENT_RANK()` → Relative position

* `CUME_DIST()` → Cumulative distribution
