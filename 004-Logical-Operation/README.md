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


## PRACTICAL - MySQL

1. AND

* SELECT all columns FROM table (employee_demographics), WHERE birth_date is greater than (>) (1985-01-01) AND gender is equal to (=) male.
    
<img width="830" height="437" alt="image" src="https://github.com/user-attachments/assets/b13f786f-1096-473f-b290-9b1cde83430c" />

2. OR

* SELECT all columns FROM table (employee_demographics), WHERE birth_date is greater than (>) (1985-01-01) OR gender is equal to (=) male.
   
<img width="918" height="525" alt="image" src="https://github.com/user-attachments/assets/1bdfd13f-9c3c-48ab-b72c-42a507dc2a92" />


2. OR & NOT
   
* SELECT all columns FROM table (employee_demographics), WHERE birth_date is greater than (>) (1985-01-01) OR gender is NOT equal to (=) male.
 
<img width="955" height="548" alt="image" src="https://github.com/user-attachments/assets/8ae8c675-27de-4fb8-858e-2c8e1f9334a1" />

3. PEMDAS in Logical Operations

* SELECT all columns FROM table (employee_demographics), WHERE (first_name is equal to (=) Leslie AND age equal to 44) OR age is greater than (>) 55.

<img width="924" height="468" alt="image" src="https://github.com/user-attachments/assets/6fb21b88-ce8a-43c2-b854-949e3916052f" />

4. LIKE STATEMENT (% and _)

* SELECT all columns FROM table (employee_demographics), WHERE first_name  LIKE 'Jer%'. Returns first_name column that starts with 'J'
  
<img width="869" height="365" alt="image" src="https://github.com/user-attachments/assets/e469fa9f-d096-429e-b5ae-a9d3ef56dca8" />

* SELECT all columns FROM table (employee_demographics), WHERE first_name  LIKE '%er%'. Returns any first_name column that has 'er" in it.

<img width="926" height="398" alt="image" src="https://github.com/user-attachments/assets/770d7d6c-a625-485c-bf53-c0789742f25f" />

* SELECT all columns FROM table (employee_demographics), WHERE first_name  LIKE 'a__'. Returns first_name column that start with 'a' and two letters after (__).

<img width="940" height="399" alt="image" src="https://github.com/user-attachments/assets/30952b46-b580-4b92-84de-d7cf60c99b1e" />




