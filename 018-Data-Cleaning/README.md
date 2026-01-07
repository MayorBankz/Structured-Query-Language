# SQL - DATA CLEANING
## DATE : 07-06-25
## TOOL - MySQL

## WHAT IS DATA CLEANING IN SQL?
Data cleaning is the process of fixing or removing incorrect, incomplete, duplicate, or inconsistent data in a database to improve data quality before analysis or reporting.

🧹 Step-by-Step Data Cleaning in SQL

Step 1: Inspect the Data

Before cleaning, understand what you are working with.

```sql
SELECT *
FROM customers;
```

Check for:
* NULL Values
* Duplicate records
* Wrong data formats
* Inconsistent texts (e.g., `lagos`, `LAGOS`, `Lagos`)

Step 2: Handle NULL values
NULLs represent missing data.

Find NULL values

``` sql
      SELECT * FROM customers
WHERE email IS NULL;
```

- Replace NULL values
  
  ```sql
    UPDATE customers
    SET email = 'not_provided'
    WHERE email IS NULL;
  ```
- Or remove rows with NULL

```sql
DELETE FROM customers
WHERE email IS NULL;
```

Step 3: Remove Duplicate Records
Duplicates can distort analysis

Find duplicates

```sql
SELECT email, COUNT(*)
FROM customers
GROUP BY email
HAVING COUNT(*) > 1;
```

Delete duplicates (example using ID)
```sql
DELETE FROM customers
WHERE id NOT IN (
    SELECT MIN(id)
    FROM customers
    GROUP BY email
);
```

Step 4: Standardize Text Data
Make text values consistent.
Convert text to uppercase or lowercase

```sql
UPDATE customers
SET city = UPPER(city);
```

Remove unwanted spaces

```sql
UPDATE customers
SET city = TRIM(city);
```

Step 5: Fix Incorrect or Inconsistent Values
Correct spelling errors or inconsistent entries.

```sql
UPDATE customers
SET city = 'LAGOS'
WHERE city IN ('Lagos ', 'lagos', 'LAGOS ');
```

Step 6: Validate Data Ranges

Ensure values fall within acceptable limits.

Example: Remove negative ages

```sql
DELETE FROM customers
WHERE age < 0;
```

Or correct them

```sql
UPDATE customers
SET age = NULL
WHERE age < 0;
```

Step 7: Format Dates Correctly

Ensure dates are consistent.

```sql
SELECT TO_DATE(order_date, 'YYYY-MM-DD')
FROM orders;
```

Step 8: Verify Cleaned Data

Always recheck after cleaning.

```sql
    SELECT COUNT(*) FROM customers;
```

Confirm:
* No unwanted NULLs
* No duplicates
* Consistent formats

### SUMMARY
Data cleaning in SQL involves:

* Inspecting the data

* Handling NULL values

* Removing duplicates

* Standardizing text

* Fixing incorrect values

* Validating ranges

* Formatting dates

* Verifying results

Clean data = accurate analysis and reliable decisions 📊
