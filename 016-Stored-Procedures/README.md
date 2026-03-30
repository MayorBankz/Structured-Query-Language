# SQL - STORED PROCEDURE
## DATE - 25-12-25
## TOOL - MySQL

---

### What is a Stored Procedure?
A stored procedure is a saved set of SQL statements stored in the database.
You can run it whenever needed instead of writing the same SQL code again and again.

Think of it like a function in programming, but for SQL.

---

### Why Use Stored Procedures?
* Reusability - – write once, use many times
* Performance - runs faster since it’s precompiled
* Security -- users can run the procedure without accessing tables directly
* Maintainability – easy to update logic in one place

---

1. Basic Stored Procedure (No Parameters)


   * Create Procedure

```sql
$$ DELIMETER

CREATE PROCEDURE GetAllCustomers()

BEGIN

    SELECT * FROM customers;

END$$

DELIMITER ;
```

* Execute Procedure

```sql
CALL GetAllCustomers();
```

2. Stored Procedure with Input Parameter
   
* Example: Get customer by ID

```sql
  DELIMITER $$

CREATE PROCEDURE GetCustomerById(IN cust_id INT)

BEGIN

    SELECT *
    FROM customers
    WHERE customer_id = cust_id;

END$$

DELIMITER ;
```

* Execute CALL GetCustomerById(3);

---

3. Stored Procedure with multiple Parameters

* Example: Customers by City

```sql
 DELIMITER $$

CREATE PROCEDURE GetCustomersByCity(IN city_name VARCHAR(50))

BEGIN

    SELECT *
    FROM customers
     WHERE city = city_name;

END$$

DELIMITER ;
```
* Execute CALL GetCustomersByCity('Lagos');

---

4. Stored Procedure for INSERT

```sql
DELIMITER $$

CREATE PROCEDURE AddCustomer(
    IN cust_name VARCHAR(100),
    IN cust_email VARCHAR(100),
    IN cust_city VARCHAR(50)
)
BEGIN
    INSERT INTO customers(name, email, city)
    VALUES (cust_name, cust_email, cust_city);
END$$

DELIMITER ;
```
* Execute CALL CheckOrderAmount(750);

---

5. Stored Procedure with IF Condition

```sql
DELIMITER $$

CREATE PROCEDURE CheckOrderAmount(IN amount DECIMAL(10,2))
BEGIN

    IF amount > 500 THEN
        SELECT 'High value order' AS Message;
    ELSE
        SELECT 'Regular order' AS Message;
    END IF;

END$$

DELIMITER ;
```
* Execute CALL CheckOrderAmount(750);

---

6. Delete Stored Procedure

```sql
DROP PROCEDURE IF EXISTS GetAllCustomers;
```

---

### STORED PROCEDURE WITH PARAMETER

Parameters allow you to pass values into a procedure

✅ Syntax

```sql
CREATE PROCEDURE procedure_name
    @param_name datatype
AS
BEGIN
    -- SQL logic
END;
```
### EXAMPLE

```sql
CREATE PROCEDURE get_customer_orders
    @customer_id INT
AS
BEGIN
    SELECT *
    FROM orders
    WHERE customerid = @customer_id;
END;
```

---

▶️ Execute
```sql
EXEC get_customer_orders @customer_id = 101;
```

---

🔹 Multiple Parameters Example

```sql
CREATE PROCEDURE get_orders_by_range
    @min_sales DECIMAL,
    @max_sales DECIMAL
AS
BEGIN
    SELECT *
    FROM orders
    WHERE sales BETWEEN @min_sales AND @max_sales;
END;
```

---

🔸 Stored Procedure with Multiple Statements
Stored procedures can run more than one SQL statements
---

```sql
CREATE PROCEDURE customer_summary
AS
BEGIN
    -- Step 1: Total sales per customer
    SELECT customerid, SUM(sales) AS total_sales
    FROM orders
    GROUP BY customerid;

    -- Step 2: Total number of orders
    SELECT COUNT(*) AS total_orders
    FROM orders;
END;
```

---

🔹 Using Variables Inside Procedure

```sql
CREATE PROCEDURE total_sales_value
AS
BEGIN
    DECLARE @total DECIMAL;

    SELECT @total = SUM(sales) FROM orders;

    SELECT @total AS total_sales;
END;
```

---

🔸 Error Handling in Stored Procedures
Used to handle errors gracefully instead of crashing
---

```sql
BEGIN TRY
    -- SQL code
END TRY
BEGIN CATCH
    -- Error handling
END CATCH
```
---

### EXAMPLE
```sql
CREATE PROCEDURE safe_insert
AS
BEGIN
    BEGIN TRY
        INSERT INTO orders (customerid, sales)
        VALUES (101, 50);
        
        SELECT 'Insert successful' AS message;
    END TRY

    BEGIN CATCH
        SELECT ERROR_MESSAGE() AS error_message;
    END CATCH
END;
```

---

### COMMON ERROR FUNCTIONS
* `ERROR_MESSAGE()` - shows error message
* `ERROR_NUMBER()` - Shows error code

---

🔸 Stored Procedure with Conditional Logic

---

```sql
CREATE PROCEDURE customer_category
    @customer_id INT
AS
BEGIN
    DECLARE @total DECIMAL;

    SELECT @total = SUM(sales)
    FROM orders
    WHERE customerid = @customer_id;

    IF @total > 100
        SELECT 'VIP' AS category;
    ELSE
        SELECT 'Regular' AS category;
END;
```

---

🔸 Updating Data Using Stored Procedure

---

### Example

```sql
CREATE PROCEDURE update_sales
    @customer_id INT,
    @new_sales DECIMAL
AS
BEGIN
    UPDATE orders
    SET sales = @new_sales
    WHERE customerid = @customer_id;
END;
```


---

⚠️ Important Notes
* Syntax may differ slightly across databases:
    * SQL Server - @param
    * MySQL - no @ inside procedure definition
* Stored procedures are stored in the database

---



* Stored procedures are saved in the database

* They can accept input parameters

* They can perform SELECT, INSERT, UPDATE, DELETE

* They improve performance and security

---

### When to Use Stored Procedures

* Repeated business logic

* Complex queries

* Secure database operations

* Backend applications (e.g., banking, ERP systems)

---

### BEST PRACTICES
* Use clear procedure names (`get_`, `update_`, etc.)
* Always handle errors (TRY...CATCH)
* Avoid unnecessary SELECT*
* Use parameters instead of hardcoding values
* Keep procedures simple and readable

---

### QUICK SUMMARY
* **Stored procedure** = Saved SQL Logic
* **Parameters** = Inputs to your procedure
* **Multiple statements** = Run many queries at once
* **Error handling** = Prevent crashes

---



### Key Points to Remember

### Practical Examples - MySQL

<img width="1008" height="459" alt="image" src="https://github.com/user-attachments/assets/66f95cd7-d567-4473-af24-9b72f4822c97" />
---
<img width="1025" height="586" alt="image" src="https://github.com/user-attachments/assets/81785250-773a-4d12-b8bd-e398ec5bfed9" />

Note: stored procedures can also be created from the "Schemas Tab" by right clicking on stored procedures and selecting create stored procedure and applying.

---

<img width="830" height="615" alt="image" src="https://github.com/user-attachments/assets/61d71af9-37c6-49fd-a6dd-cd2bfddc6cc3" />

---
<img width="812" height="425" alt="image" src="https://github.com/user-attachments/assets/289b652b-7fb6-4cee-a98a-2c7e9de6e673" />



