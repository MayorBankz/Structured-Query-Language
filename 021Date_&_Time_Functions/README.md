# SQL Date & Time Functions (Easy to Understand Documentation)
## Date: 10/02/2026
## TOOL: MySQL

---

## OVERVIEW

Date and time functions in SQL are used to extract, format, calculate, and validate dates and times. They are essential for reporting, analytics, auditing, and business logic.
This documentation is written in simple language and focuses mainly on SQL Server-style functions, while still being useful for general SQL understanding.

---

1. Date & Data Types


| Data Type | Description | Example |
| ------ | -------- | -------- |
| `Date` | Stores date only | `2026-02-10` |
| `Time` | Stores time only | `14:30:00` |
| `DATETIME` | Date and time | `2026-02-10 14:30:00.000` |
| `DATETIME2` | More precise datetime | `2026-02-10 14:30:00.000` |
| `TIMESTAMP` | Auto-generated versioning value | Not a real date |

---

2. Part Extraction Functions

These functions extract specific parts of a date, such as day, month, or year.
---

a. DAY(), MONTH(), YEAR()

```sql
SELECT DAY(Order_date), MONTH(Order_date), YEAR(Order_date)
FROM Orders;
```

| Function | Returns |
| -------- | -------- |
| `Day()` | Day number |
| `MONTH()` | Month number |
| `YEAR()` | Year |

---

b. DATEPART()

Returns a specific part of the date based on the unit provided .

```sql
SELECT DATEPART(month, order_date)
FROM orders;
```

### Common Units:
* `day`
* `month`
* `year`
* `hour`
* `minute`

---

c. DATENAME()

Returns the name of the date part instead of a number.

```sql
SELECT DATENAME(month, order_date)
FROM Orders;
```

Output Example: `February`

---

d. DATETRUNC()
Truncates a date to the start of a given unit.
```sql
SELECT DATETRUNC(month, order_date)
FROM Orders;
```

Example result: `2026-02-01 00:00:00`

---

e. EOMONTH()

Returns the last day of the month
```sql
SELECT EOMONTH((order_date)
FROM orders;
```
Example Result: `2026-02-28`

---

3. FORMAT & CASTING FUNCTIONS

These functions control how dates appear and how data types are changed

---

a. `FORMAT()`

Formats date/time into a readable string

```sql
SELECT FORMAT(Order_date, `dd MMM yyyy`)
FROM Orders;
;
```

Output: `10 Feb 2026`

---

b. `CONVERT()`

Converts data from one type to another with style options.
```sql
SELECT CONVERT(VARCHAR, order_date, 'dd/mm/yyyy')
FROM Orders;
```

---

c. `CAST()`
Standard SQL method for type conversion.
```sql
SELECT CAST(order_date as DATE)
FROM Orders;
```
---

4. DATE CALCULATIONS

Used to add or subtract time and calculate differences.

a. `DATEADD()`
Adds or subtracts a time interval.

```sql
SELECT DATEADD(day, 7, order_date)
FROM Orders;
```

### Common Intervals
* `day`
* `month`
* `year`
* `hour`

---

b. `DATEDIFF()`

Returns the difference between two dates in a specified unit.

```sql
SELECT DATEDIFF(day, order_date, GETDATE())
FROM Orders;
```

---

5. DATE VALIDATION FUNCTION
ISDATE()
Checks whether a value is a valid date.
```sql
SELECT ISDATE(`2026-02-10`); -- Returns 1
SELECT ISDATE(`2026-99-99'); -- Returns 0
```

| Result | Meaning |
| ------ | ------- |
| `1` | Valid date |
| `0` | Invalid date |

---

6. Practical Business Examples

a. Get records for the current month 

```sql
SELECT *
FROM Orders
WHERE DATETRUNC(month, order_date) =DATETRUNC(month, GETDATE());
```

---

b. Get last day of current month

```sql
SELECT EOMONTH(GETDATE());
```

---

c. Calculate customer order age (in days)

```sql
SELECT order_id, DATEDIFF(day, order_date, GETDATE()) as order_age
FROM Orders;
```

---

### COMMON MISTAKES TO AVOID 
* :x: Treating dates as plain text
* ✅ Always use proper date data types 
* :x: Using `FORMAT()` in filters (slow performance)
* ✅  Use it only for display
* :x: Forgetting that `DATEDIFF()` counts boundaries
* ✅ Always test with real data

---

### SUMMARY 
* PART EXTRACTION: `DAY`, `MONTH`, `YEAR`, `DATEPART`, `DATENAME`, `DATETRUNC`, `EOMONTH`
* FORMATTING & CASTING: `FORMAT`, `CONVERT`, `CAST`
* Calculations: `DATEADD`, `DATEDIFF`
* VALIDATION: `ISDATE`
