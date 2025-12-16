# SQL- CASE STATEMENTS
## DATE - 16-12-2025
## TOOL - MySQL

## CASE STATEMENTS

The CASE statement in SQL is used to apply conditional logic.
It works like an IF–ELSE statement, allowing you to return different values based on conditions.

### WHY USE CASE?

* Categorize data

* Apply conditions in queries

* Create custom output columns

* Improve readability of query results

### SYNTAX 
1. SIMPLE CASE - Used when comparing a single column to multiple values.

   CASE column

     WHEN value1 THEN result1

    WHEN value2 THEN result2


 ELSE default_result

END

2. SEARCHED CASE - Used when evaluating different conditions.

CASE
   
    WHEN condition1 THEN result1
    
    WHEN condition2 THEN result2
    
    ELSE default_result
END

### Example - Categorizing Data

SELECT customer_name,
       CASE
          
           WHEN total_purchase >= 1000 THEN 'Premium'
           WHEN total_purchase >= 500 THEN 'Regular'
           ELSE 'Basic'
       END AS customer_category
FROM customers;

### Explanation
Customers are classified as Premium, Regular, or Basic based on their total purchase amount.

## Example 2 - Using CASE with Numbers

SELECT score,
       CASE
          
           WHEN score >= 70 THEN 'Pass'
           ELSE 'Fail'
          END AS result
FROM students;

3. CASE in ORDER BY

   SELECT name, status
 FROM users
ORDER BY
CASE
    WHEN status = 'Active' THEN 1
    ELSE 2
END;

## Explanation

Active users are listed first.

### Important Notes
* CASE must end with END
* ELSE is optional (returns NULL if omitted)
* Can be used in SELECT, WHERE, ORDER BY and HAVING.

## SUMMARY

The CASE statement adds decision-making ability to SQL queries, making results more meaningful and easier to interpret.

## Practical Example - CASE STATEMENTS  

* SELECT the columns (first_name, last_name) using the CASE statement for when age is greater than or equals to 30, THEN we can say this person is 'young' END, FROM the table employee_demographics

<img width="835" height="774" alt="image" src="https://github.com/user-attachments/assets/a7cc55c3-768a-43ad-b223-34554cf96a9a" />
<img width="856" height="774" alt="image" src="https://github.com/user-attachments/assets/6141018c-0a61-48f4-8f3c-c8eb8c0ec6ba" />
<img width="893" height="701" alt="image" src="https://github.com/user-attachments/assets/c03b73bb-4e50-4635-85ec-1433fb8af073" />

* SECOND SCENARIO - Pay Increase
-- Pay increase and bonus
-- < 50000 = 5% increase
-- > 50000 = 7% increase
-- Finance = 10% bonus

* When salary is less than 50000, 5% increase

<img width="872" height="626" alt="image" src="https://github.com/user-attachments/assets/25e71aab-ded6-4495-b62e-ff011af449b1" />

* When salary is greater than 50000, 7% increase

<img width="999" height="667" alt="image" src="https://github.com/user-attachments/assets/f60c70eb-ffbd-46c1-bda6-1ac0567bb5d4" />

* when salary is less than 50000, 5% increase and when salary is greater than 50000, 7% increase

<img width="1023" height="671" alt="image" src="https://github.com/user-attachments/assets/490fec7b-d518-4585-8324-981d8a3c6287" />

* when department is finance, 10% bonus

<img width="967" height="669" alt="image" src="https://github.com/user-attachments/assets/39e3fcaf-1818-4f67-8198-5089aaca7f56" />



  







