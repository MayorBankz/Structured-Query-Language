# SQL - GROUP BY & ORDER BY
## Date - 10-12-2025
## Tool - MySQL


## Group by & Order by

SQL provides the GROUP BY and ORDER BY clauses to help organize and arrange query results.
They are commonly used when summarizing data and controlling the final output format.

## GROUP BY

The GROUP BY clause is used to group rows that have the same values in specified columns.
It is mostly used together with aggregate functions like:

* COUNT()
* SUM()
* AVG()
* MAX()
* MIN()

### Purpose 

* To summarize or aggregate data.

* To create grouped reports (e.g., sales per region, number of users per country, etc.).

### Example

SELECT Country, COUNT(*) AS TotalCustomers

FROM Customers

GROUP BY Country;

### What it does:
Groups all customers by country and returns how many customers are in each country.

## ORDER BY

The ORDER BY clause is used to sort the result of a query.

You can sort:

* ASC → ascending (default)

* DESC → descending

### Example

SELECT * 

FROM Products

ORDER BY Price DESC;

### What it does:

Lists all products, starting from the most expensive to the cheapest.

## USING GROUP BY and ORDER BY Together

You can first group the data, then order the grouped results.

### Example

SELECT Department, COUNT(*) AS StaffCount

FROM Employees

GROUP BY Department

ORDER BY StaffCount DESC;

### What it does:

* Groups employees by department.

* Counts the number of staff in each department.

* Sorts the result from highest to lowest


## SUMMARY

| Clause | What it does | Example Use |
| ------ | ------------ | ----------- |
| GROUP BY | Groups rows with the same value | Group customers by country |
| ORDER BY | Sorts result (ASC or DESC) | Sort products by price |
| Both Together | Aggregates & Organizes data | Count staff per department then sort |



