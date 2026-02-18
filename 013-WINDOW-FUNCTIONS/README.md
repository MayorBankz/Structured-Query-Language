# SQL - WINDOWS FUNCTION 
## DATE - 18-12-25
## TOOL - MySQL

## WINDOWS FUNCTION IN SQL

### What is a Window Function?

A Window Function performs a calculation across a set of related rows (called a window) without collapsing the rows into a single result.

👉 Unlike GROUP BY, window functions keep each row visible while still allowing calculations across multiple rows.

### BASIC SYNTAX

function_name (expression)

OVER (

    PARTITION BY column_name
    
    ORDER BY column_name
)

### KEY COMPONENTS

* OVER() - Defines the window (group of rows) the function works on.
* PARTITION BY - Divides rows into groups (optional).
* ORDER BY - Orders rows within each partition (optional).


### COMMON WINDOW FUNCTIONS
 | FUNCTION | DESCRIPTION |
 | -------- | ----------- |
 | ROW_NUMBER() | Assigns a unique number to each row |
 | RANK() | Assigns rank with gaps |
 | DENSE_RANK() | Assigns rank without gaps |
  | SUM() | Running or partitioned total |
  | AVG() | Running or partitioned average |
  | COUNT() | Count over a window |
  | LAG() / LEAD() | Access previous or next row values | 

### SIMPLE EXAMPLES

1. Assign row numbers

     SELECT name, salary,

ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num

FROM employees;

2. Rank employees by salary per department
   ```sql

           SELECT name, department, salary,

            RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dept_rank

            FROM employees;
   ```

4. Running total
```sql
            SELECT date, amount,

               SUM(amount) OVER (ORDER BY date) AS running_total

             FROM sales;
```
---

### WINDOWS FUNCTION VS GROUP BY 

| WINDOW FUNCTION | GROUP BY |
| --------------- | -------- |
| Keep all rows | Reduces rows |
| Best for ranking, running totals | Best for summaries |
| More flexible | Simpler aggregation |
---
### WHEN TO USE WINDOW FUNCTIONS 
* Ranking data
* Running totals or averages
* Comparing rows within a group
* Finding previous or next values
---

### FRAME CLAUSE SYNTAX & EXAMPLES (ROWS)

General Syntax
```sql
FUNCTION() OVER (
    PARTITION BY column
    ORDER BY column
    ROWS BETWEEN frame_start AND frame_end
)
```
---

1️⃣ UNBOUNDED PRECEDING → CURRENT ROW
✅ Running Total

```sql
ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
```

Example
```sql
SELECT order_date,
       sales,
       SUM(sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_total
FROM orders;
```
👉 Includes all rows from the first row up to the current row.

---
2️⃣ n PRECEDING → CURRENT ROW

✅ Moving Window (Previous Rows + Current)
```sql
ROWS BETWEEN n PRECEDING AND CURRENT ROW
```

Example (3-row moving average)

```sql
SELECT order_date,
       sales,
       AVG(sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
       ) AS moving_avg
FROM orders;
```
👉 Includes current row + 2 rows before it.

---

3️⃣ CURRENT ROW → n FOLLOWING
✅ Current Row + Next Rows

```sql
ROWS BETWEEN CURRENT ROW AND n FOLLOWING
```

---

🔹 Example
```sql
SELECT order_date,
       sales,
       SUM(sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN CURRENT ROW AND 2 FOLLOWING
       ) AS forward_sum
FROM orders;
```
👉 Includes current row + next 2 rows.

---

4️⃣ n PRECEDING → n FOLLOWING
✅ Centered Window

🔹 Syntax
```sql
ROWS BETWEEN n PRECEDING AND n FOLLOWING
```

🔹 Example
```sql
SELECT order_date,
       sales,
       AVG(sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING
       ) AS centered_avg
FROM orders;
```
Includes:

* 1 row before

* Current row

* 1 row after

---

5️⃣ CURRENT ROW → CURRENT ROW
✅ Current Row Only
```sql
ROWS BETWEEN CURRENT ROW AND CURRENT ROW
```
🔹 Example
```sql
SELECT order_date,
       sales,
       SUM(sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN CURRENT ROW AND CURRENT ROW
       ) AS current_only
FROM orders;
```
👉 Only includes the current row. 
(Practically same as just selecting the column.)
---
6️⃣ UNBOUNDED PRECEDING → UNBOUNDED FOLLOWING
✅ Entire Partition
```sql
ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
```
🔹 Example
```sql
SELECT employeeid,
       department,
       salary,
       SUM(salary) OVER (
           PARTITION BY department
           ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
       ) AS dept_total
FROM employees;
```
👉 Includes all rows in each partition.

---

7️⃣ n PRECEDING → n PRECEDING
✅ Specific Previous Row Only
🔹 Syntax
```sql
ROWS BETWEEN n PRECEDING AND n PRECEDING
```
Example (Previous row only)
```sql
SELECT order_date,
       sales,
       SUM(sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN 1 PRECEDING AND 1 PRECEDING
       ) AS previous_row_value
FROM orders;
```
👉 Includes only the previous row.

---

🧠 Quick Reference Table

| Frame | Meaning |
| ----- | ------- |
| UNBOUNDED PRECEDING - CURRENT ROW | Running Total |
| CURRENT ROW - n FOLLOWING | Moving window |
| n PRECEDING - CURRENT ROW | Forward-looking window |
| CURRENT ROW → CURRENT ROW | Current row only |
| n PRECEDING → n FOLLOWING | Centered window |
| UNBOUNDED PRECEDING → UNBOUNDED FOLLOWING | Entire partition |
| n PRECEDING → n PRECEDING | Specific previous row |

### SUMMARY 

Window function let you analyze data across related rows while keeping each row intact, making them powerful for analytics and reporting.

## Practical Examples - MySQL

1. GROUP BY function - In this example, we look at the group by - compare the changes here in the GROUP BY function with the window function

   <img width="743" height="351" alt="image" src="https://github.com/user-attachments/assets/76c5f33d-f770-4b6c-ae7c-4ab97c0598fe" />
---
2. WINDOW FUNCTION - window is almost similar to the GROUP BY function in that it produces the same result as the GROUP BY function, but the output format of the result is different. 

   <img width="784" height="490" alt="image" src="https://github.com/user-attachments/assets/78d756f7-ae77-4f9e-8b0a-a79642c86b2b" />
---
* Another thing to note is in GROUP BY function, you can only GROUP BY a column, but in WINDOW FUNCTION you can group as many columns as possible

  <img width="899" height="445" alt="image" src="https://github.com/user-attachments/assets/ee8253d7-6901-48d5-8416-d21d2e505ab3" />
---
3. WINDOW FUNCTION (ROLLING TOTAL) - Starts at a specific value and add on values from subsequent rows based off of your partition

   <img width="877" height="416" alt="image" src="https://github.com/user-attachments/assets/82fdf0d3-82d6-43f2-b276-0b9dbc667f69" />
---
4. ROW_NUMBER

   <img width="744" height="483" alt="image" src="https://github.com/user-attachments/assets/8c080d81-ca48-4bad-b931-6dd679f94278" />
---
4 ROW_NUMBER - PARTITION BY

<img width="774" height="464" alt="image" src="https://github.com/user-attachments/assets/e8d8c7bc-f93e-4c08-b62e-1479ee642233" />

   <img width="800" height="566" alt="image" src="https://github.com/user-attachments/assets/23aea767-d35e-4ab7-821f-5530d28bb6d2" />

---

5. RANK

   <img width="904" height="525" alt="image" src="https://github.com/user-attachments/assets/921fe5b5-377a-4195-a916-4bf66490e057" />

---

6. DENSE_RANK

   <img width="834" height="406" alt="image" src="https://github.com/user-attachments/assets/cf049395-2106-4948-80ec-93b914527912" />






