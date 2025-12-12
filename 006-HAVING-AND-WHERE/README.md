# SQL - WHERE and HAVING
## Date - 12-12-2025
## Tool - MySQL


## Understanding WHERE and HAVING

When working with SQL, you will often need to filter data.

WHERE and HAVING both helps you filter records - but they are used at different stages in a query.

### WHERE CLAUSE

Purpose:

To filter rows before any grouping or aggregation happens .

### When is WHERE used?
* When you want to filter individual rows.
* Before using functions like SUM(), COUNT(), AVG(), etc.

Example 

Get all customers from the city Lagos.

SELECT *

FROM Customers

WHERE City = 'Lagos';

Here, SQL checks each row and only returns rows that meet the condition.


## HAVING CLAUSE

### Purpose 

To filter groups after aggregation

### When is HAVING used?

* When you use GROUP BY.

* When you filter results based on aggregate functions like SUM(), COUNT(), MAX(), etc.

### Example 

Get only those cities where the number of customers is more than 5.

SELECT City, COUNT(*) AS TotalCustomers

FROM Customers

GROUP BY City

HAVING COUNT(*) > 5;
Here:

* SQL groups customers by city.

* Then uses HAVING to filter only cities with more than 5 customers.

## Simple Difference Between WHERE and HAVING

| Feature | WHERE | HAVING |
| ------- | ----- | ------ |
| filters row | Yes | No |
| Filters group | No | Yes |
| Used before GROUP BY | Yes | No |
| Used after GROUP BY | No | Yes |
| Works with aggregate functions (SUM, COUNT, etc.) | No | 

### Example - Showing Both Together 
Find cities where:

* Customers are active (Status = 'Active') → filter using WHERE

* And each city has more than 10 active customers → filter using HAVING

Explanation 

* WHERE removes all inactive customers first.

* GROUP BY groups remaining rows by city.

* HAVING filters cities with more than 10 active customers.

Key Takeaways (Easy Memory Trick)

* WHERE = Filter rows first

* GROUP BY = Create groups

* HAVING = Filter groups after aggregation


## Practical - 
### HAVING

* Select the column gender, and aggregate using AVG(age) from table (employee_demographics) then group by gender HAVING AVG(age) greater than 40
  
<img width="915" height="478" alt="image" src="https://github.com/user-attachments/assets/c8a88cb1-44f6-4e1e-9e51-4e59de992506" />


### WHERE 

* Select the column occupation, and aggregate using AVG(salary) from table (employee_salary) WHERE occupation LIKE '%manager% group by occupation

<img width="891" height="477" alt="image" src="https://github.com/user-attachments/assets/b70630af-29d2-44b9-bf49-b6ae2a776c7d" />


### WHERE and HAVING 

* WHERE is used before the GROUP BY function
* HAVING is used after the GROUP BY function

<img width="851" height="451" alt="image" src="https://github.com/user-attachments/assets/768dbc7e-9a22-4162-827a-3c28ac535ff6" />




