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

```sql
SELECT Country, COUNT(*) AS TotalCustomers
FROM Customers
GROUP BY Country;
```

### What it does:
Groups all customers by country and returns how many customers are in each country.

## ORDER BY

The ORDER BY clause is used to sort the result of a query.

You can sort:

* ASC → ascending (default)

* DESC → descending

### Example

```sql
SELECT * 
FROM Products
ORDER BY Price DESC;
```

### What it does:

Lists all products, starting from the most expensive to the cheapest.

## USING GROUP BY and ORDER BY Together

You can first group the data, then order the grouped results.

### Example

```sql
SELECT Department, COUNT(*) AS StaffCount
FROM Employees
GROUP BY Department
ORDER BY StaffCount DESC;
```

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


## Practical - GROUP BY and ORDER BY 

* Database - Parks_and_recreation
* Table 1 - employee_demographics
* Table 2 - employee_salary

## Table 1 - employee_demographics

<img width="917" height="539" alt="image" src="https://github.com/user-attachments/assets/cd2c85a2-e809-4963-be76-b9662f419afb" />

## Table 2 - employee_salary

<img width="877" height="494" alt="image" src="https://github.com/user-attachments/assets/6cf621a4-75f3-4ad9-90e0-1f518eb64d6e" />

## GROUP BY

* select the column gender from the table (employee_demographics) and perform the aggregate function average age (AVG(age))
  
<img width="940" height="484" alt="image" src="https://github.com/user-attachments/assets/20070474-8a25-403c-a253-833b51c2c773" />

<img width="817" height="411" alt="image" src="https://github.com/user-attachments/assets/1d23f37f-f584-4ec0-b420-5f381f0e469f" />

## ORDER BY

Note: This query is run in ascending order by default

* Select all the columns from table (employee_demographics) and order by the column (first_name) in descending order
  
<img width="887" height="549" alt="image" src="https://github.com/user-attachments/assets/a13d7b6a-2fe5-4b4e-a938-d9b79cf28e81" />


