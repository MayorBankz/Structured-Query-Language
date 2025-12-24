# SQL - TEMPORARY TABLE
## DATE - 24-12-25
## TOOL - MySQL

### What is a Temporary Table?

A Temporary Table is a table that is created to store data temporarily during a database session or query execution.
It is mainly used to hold intermediate results for processing or analysis.

Once the session ends (or the table is dropped), the temporary table is automatically removed.

### Why Use Temporary Tables?

Temporary tables are useful when:

* You need to store intermediate results

* Data needs to be reused across multiple queries

* Complex calculations are involved

* Performance improvement is needed for large datasets

## Types of Temporary Tables

Depending on the database system:

1. Local Temporary Table

    * Visible only to the current session
    * Automatically dropped when the session ends
2. Global Temporary Table
     * Visible to all sessions

     * Data is session-specific or transaction-specific

    * Table structure remains, but data is cleared

  ### BASIC SYNTAX (LOCAL TEMPORARY TABLE)

  
    CREATE TEMPORARY TABLE temp_orders (
    
    order_id INT,
    
    total_amount DECIMAL(10,2)
);

### INSERT DATA

INSERT INTO temp_orders

SELECT order_id, total_amount

FROM orders

WHERE total_amount > 500000;

### USE THE TABLE

SELECT * FROM temp_orders;

### DROP THE TABLE 

DROP TABLE temp_orders;

### TEMPORARY TABLE VS REGULAR TABLE
| Temporary Table | Regular Table |
| --------------- | ------------- |
| Exists temporarily | Exists permanently |
| Session-based | Stored in the database |
| Used for intermediate data | Used for long-term data |

### TEMPORARY TABLE vs CTE
| Temporary table | CTE |
| --------------- | --- |
| Can be reused across multiple queries | Used within a single query |
| Can have indexes | Cannot have indexes |
| Stored temporarily in database | Exists only during query execution |

### Key Points to Remember 

* Temporary tables are not permanent
* They improve query organization and performance
* Ideal for handling complex data processing
* Automatically removed when the session ends

### When to use Temporary Tables
Use temporary tables when:

* You need data across multiple SQL statements
* Working with large or complex transformations
* Performance tuning is required
  
