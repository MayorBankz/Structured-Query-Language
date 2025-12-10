# SQL - Logical Operations
## Date - 09-12-25
## Tool - MySQL

## Logical Operations 

Logical operations in SQL are used to combine, filter, and control how conditions work inside a query—especially in the WHERE clause. They help SQL decide which rows should be returned.

1. AND - The AND operator is used when all conditions must be true.

Example:

SELECT * 

FROM Customers

WHERE Country = 'USA'

  AND Age > 25;
This returns customers who are both in the USA and older than 25.

2. OR - The OR operator is used when at least one condition must be true.

 Example 

 SELECT * 
 
 FROM Customers

WHERE City = 'Lagos'
  
   OR City = 'Abuja';
This returns customers who are either in Lagos or Abuja.

3. NOT - The NOT operator is used to exclude a condition.

Example 

SELECT *

FROM Products

WHERE NOT Category = 'Electronics';

This returns products that are not in the Electronics category.

4. BETWEEEN - Used to check if a value falls within a range (inclusive).

Example

SELECT * 

FROM Orders

WHERE OrderAmount BETWEEN 1000 AND 5000;

Returns orders with amount from 1000 to 5000.

5. IN - Used to match a value against multiple possible values.

Example 

SELECT * 

FROM Employees

WHERE Department IN ('HR', 'Finance', 'IT');

Returns employees in HR, Finance, or IT.

6. LIKE - Used for pattern matching, especially with wildcards % and _.

Example 

SELECT * 

FROM Customers

WHERE Name LIKE 'J%';

Returns customers whose names start with ‘J’.

7. IS NULL / IS NOT NULL - Used to check for NULL values (empty or unknown data).

SELECT * 

FROM Students

WHERE Email IS NULL;

Returns students without an email address.


## SUMMARY TABLE

| Logical Operation | Meaning | Example |
| ----------------- | ------- | ------- |
| AND | All conditions must be true | Country = 'USA' AND Age > 25 |
| OR | At least one condition is true | City = 'Lagos' OR City = 'Abuja' |
| NOT | Excludes a condition | NOT category = 'Electronics' |
| BETWEEN | Value within a range | Amount BETWEEN 1000 AND 5000 |
| IN | Match one of several values | Department IN ('HR','IT') |
| LIKE | Pattern matching | Name like 'j%' |
| IS NULL | Check for empty value | Email is NULL |
