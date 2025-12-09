# SQL - PEMDAS + DISTINCT
* Date - 08-12-2025
* Practical Software - MySQL


## PEMDAS (Order of Operation)
<b>PEMDAS</b> is a rule used to determine the order in which mathematical calculations are performed. 
It stands for:

| Letter	| Meaning |
| ------ | -------- |
| P |	Parentheses |
| E	| Exponents |
| M |	Multiplication |
| D |	Division |
| A	| Addition |
| S	| Subtraction |

* Multiplication and Division have the same priority → perform left to right.
* Addition and Subtraction also have the same priority → left to right.

Example
8 + 2 * ( 5-1)
1. Parentheses - (5 - 1) = 4
2. Multiplication - 2 x 4 = 8
3. Addition - 8 + 8 = 16

## DISTINCT 

DISTINCT is used in SQL to remove duplicate values from a result set.

It ensures that only unique values are returned.

### Simple Example 
Assume you have a table called customers 

| Customer Name | Country |
| ------------- | ------- |
| John | USA |
| Sarah | USA |
| Michael | Canada |
| John | USA |

<i>SELECT DISTINCT</i> Country

<i>FROM</i> Customers;

Result 
| Country |
| ------ |
| USA |
| Canada |

* SQL will return only unique countries, even though "USA" appears multiple times.

### Another example with multiple columns
SELECT DISTINCT <i>Country, CustomerName</i>

FROM <i>Customers;</i>

* This returns unique combinations of Country + CustomerName


## Practical - PEMDAS + DISTINCT


* SELECT the columns first_name, last_name, birth_date, age FROM table (employee_demographics). another column will be created in this case because of the arithmetic (PEMDAS)

<img width="964" height="554" alt="image" src="https://github.com/user-attachments/assets/290fc333-bd45-4bee-afbc-b74aa452d14b" />

* SELECT unique values (DISTINCT) from the column (gender)

<img width="1007" height="469" alt="image" src="https://github.com/user-attachments/assets/43cca331-5bcf-4d70-b329-9f5a9efb3c21" />





