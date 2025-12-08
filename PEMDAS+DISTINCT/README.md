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



