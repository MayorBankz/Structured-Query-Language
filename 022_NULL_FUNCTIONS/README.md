# NULL FUNCTIONS
## DATE: 12-02-2026
## TOOL: MySQL

---

📌 WHAT IS NULL IN SQL?
`NULL` represents missing, unknown, or not available data.

It is not the same as:
* `0`
* Empty string `''`
* `FALSE`

Because `NULL` means <i>"no value"</i>, SQL provides special functions to handle it safely.

---

### Common NULL functions in SQL

1. `IS NULL` - Checks if a column contains a NULL vaue

### Example 

```sql
SELECT *
FROM customers
WHERE email IS NULL;
```

O/P: Returns customers without an email address

---

2. `IS NOT NULL` - Checks if a column has a value (not null)

### Example
```sql
SELECT *
FROM customers
WHERE phone IS NOT NULL;
```

O/P: Returns customers with a phone number

---

3. `IF NULL()` (MySQL) - Replaces NULL with a specified value.

### Syntax

```sql
IFNULL(column, replacement_value)
```

### Example

```sql
SELECT 
  first_name,
  IFNULL(phone, 'Not Provided') AS phone
FROM customers;
```

O/P: Shows "Not Provided" when phone is NULL

---

4. `COALESCE` - Replaces the first non-NULL value from a list

### Syntax

```sql
COALESCE(value1, value2, value3, ...)
```

### Example 
```
SELECT 
  first_name,
  COALESCE(phone, email, 'No Contact Info') AS contact
FROM customers;
```

O/P: If phone is NULL - uses email
     If both are NULL - shows `No Contact Info`
---

5. `NULLIF()` - Returns NULL if two values are equal

### Syntax 
```sql
NULLIF(value1, value2)
```

### Example:

```sql
SELECT NULLIF(score, 0) AS score
FROM results;
```

O/P: Converts `0` to `NULL`
Useful to avoid division errors 

---

6. Handling NULL in Calculations - NULL values can break calculations if not handled.

### Example(Bad):
```sql
SELECT price * discount
FROM products;
```

❌ Returns NULL if discount is NULL

### Example (Good) 
```sql
SELECT price * IFNULL(discount, 0)
FROM products;
```

✅ Safely calculates values

---

⚠️ Important Rules About Null
* ❌ `NULL = NULL` --- FALSE
* ❌ `NULL != NULL` --- FALSE
* ✅ Always use `IS NULL` or `IS NOT NULL`
* NULL values are ignored in functions like `COUNT(column)`

---

### COUNT with NULL Example

```sql
SELECT COUNT(phone) FROM customers;
```
✅ Counts only non-NULL phone numbers

--- 

```sql
SELECT COUNT(*) FROM customers;
```
✅ Count all rows, including NULLs

--- 

### WHEN TO USE NULL FUNCTIONS

Use NULL functions when:
* Data is missing
* You want default values
* You are doing calculations
* You want clean reports

---

### SUMMARY TABLE
| Function | Purpose |
| -------- | ------- |
| `IS NULL` | Check for NULL |
| `IS NOT NULL` | Check for values |
| `IFNULL` | Replace NULL |
| `COALESCE` | First non-NULL value | 
| `NULLIF` | Convert value to NULL |
