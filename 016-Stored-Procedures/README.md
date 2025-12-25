# SQL - STORED PROCEDURE
## DATE - 25-12-25
## TOOL - MySQL

### What is a Stored Procedure?
A stored procedure is a saved set of SQL statements stored in the database.
You can run it whenever needed instead of writing the same SQL code again and again.

Think of it like a function in programming, but for SQL.

### Why Use Stored Procedures?
* Reusability - – write once, use many times
* Performance - runs faster since it’s precompiled
* Security -- users can run the procedure without accessing tables directly
* Maintainability – easy to update logic in one place

1. Basic Stored Procedure (No Parameters)


   * Create Procedure

```sql
  DELIMITER $$

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

6. Delete Stored Procedure

```sql
DROP PROCEDURE IF EXISTS GetAllCustomers;
```

### Key Points to Remember

* Stored procedures are saved in the database

* They can accept input parameters

* They can perform SELECT, INSERT, UPDATE, DELETE

* They improve performance and security

### When to Use Stored Procedures

* Repeated business logic

* Complex queries

* Secure database operations

* Backend applications (e.g., banking, ERP systems)

### Practical Examples - MySQL

<img width="1008" height="459" alt="image" src="https://github.com/user-attachments/assets/66f95cd7-d567-4473-af24-9b72f4822c97" />

<img width="1025" height="586" alt="image" src="https://github.com/user-attachments/assets/81785250-773a-4d12-b8bd-e398ec5bfed9" />

Note: stored procedures can also be created from the "Schemas Tab" by right clicking on stored procedures and selecting create stored procedure and applying.

<img width="830" height="615" alt="image" src="https://github.com/user-attachments/assets/61d71af9-37c6-49fd-a6dd-cd2bfddc6cc3" />
<img width="812" height="425" alt="image" src="https://github.com/user-attachments/assets/289b652b-7fb6-4cee-a98a-2c7e9de6e673" />



