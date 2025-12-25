# SQL - TRIGGERS AND EVENTS
## DATE - 25-12-25
## TOOL - MySQL

### WHAT IS A TRIGGER?

A trigger is a set of SQL statements that automatically runs when a specific action happens on a table.

Triggers run:

* BEFORE or AFTER

* `INSERT`, `UPDATE`, or `DELETE`

👉 You don’t call a trigger manually — it runs automatically.

### WHY USE TRIGGERS?

* Automatically enforce business rules

* Maintain audit logs

* Validate or modify data before saving

* Keep tables in sync

### TRIGGER SYNTAX
```sql
CREATE TRIGGER trigger_name
BEFORE | AFTER INSERT | UPDATE | DELETE
ON table_name
FOR EACH ROW
BEGIN
    -- SQL statements
END; **

```

### Example 1: BEFORE INSERT Trigger
* Prevent Negative Salary
  
```sql
DELIMITER $$

CREATE TRIGGER before_employee_insert
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    IF NEW.salary < 0 THEN
        SET NEW.salary = 0;
    END IF;
END$$

DELIMITER ;

```

### Example 2: AFTER INSERT TRIGGER (Audit Log)
* Log new orders

```sql
DELIMITER $$

CREATE TRIGGER after_order_insert
AFTER INSERT ON orders
FOR EACH ROW
BEGIN
    INSERT INTO order_logs(order_id, action_date)
    VALUES (NEW.order_id, NOW());
END$$

DELIMITER ;
```

### Example 3: AFTER UPDATE TRIGGER

```sql 
DELIMITER $$

CREATE TRIGGER after_price_update
AFTER UPDATE ON products
FOR EACH ROW
BEGIN
    INSERT INTO price_history(product_id, old_price, new_price)
    VALUES (OLD.product_id, OLD.price, NEW.price);
END$$

DELIMITER ;

```

### Trigger Keywords
* `New.Column_name` --- new value
* `Old.column_name` --- old value
* `BEFORE/AFTER`
* `INSERT / UPDATE / DELETE`

### Delete a Trigger 

```sql
DROP TRIGGER IF EXISTS after_order_insert;
```

## EVENTS IN MySQL
What is an Event?

An Event is a scheduled SQL task that runs automatically at a specific time or interval.

👉 Similar to a cron job in Linux.

Why Use Events?

* Automated clean-ups

* Periodic reports

* Scheduled updates

* Data archiving

### ENABLE EVENT SCHEDULER
```sql
SET GLOBAL event_scheduler = ON;
```

### EVENT SYNTAX
```sql
CREATE EVENT event_name
ON SCHEDULE schedule
DO
BEGIN
    -- SQL statements
END;
```

### EXAMPLE 1: One-Time Event
Delete logs after a date

```sql
CREATE EVENT delete_old_logs
ON SCHEDULE AT '2025-01-01 00:00:00'
DO
    DELETE FROM logs WHERE log_date < '2024-01-01';
```

### Example 2: Repeating Event
* Daily Cleanup

```sql
CREATE EVENT daily_cleanup
ON SCHEDULE EVERY 1 DAY
STARTS CURRENT_TIMESTAMP
DO
    DELETE FROM sessions
    WHERE last_active < NOW() - INTERVAL 7 DAY;
```

### EXAMPLE 3: Monthly Report Update
```sql
CREATE EVENT monthly_sales_update
ON SCHEDULE EVERY 1 MONTH
DO
    UPDATE reports
    SET last_updated = NOW();
```

### DELETE AN EVENT

```sql
DROP EVENT IF EXISTS daily_cleanup;
```

### TRIGGERS VS EVENTS (QUICK COMPARISON)

| Feature | Trigger | Event |
| ------- | ------- | ------ |
| Runs automatically | Yes | Yes |
| Based on table action | Yes | No |
| Time-based | No | Yes |
| Manual Execution | No | Yes |
| Use Case | Data validation, logging | Scheduling |


### Key Takeaways

* Triggers react to table changes
* Events run on a schedule
* Both help automate database tasks
* Events must have the scheduler enabled


## PRACTICAL EXAMPLE

1. TRIGGER

<img width="1010" height="790" alt="image" src="https://github.com/user-attachments/assets/e04b11be-b968-44d5-8b01-4410a8d33864" />

2. EVENTS

<img width="975" height="667" alt="image" src="https://github.com/user-attachments/assets/f86e9e1f-1b04-4e3f-ab25-beffa5aa85be" />

Note: In the case where 'EVENT' doesn't run. To check

* Run the code

  ```sql
      show variables like 'event%;
  ```
  * If event is off then turn ON

Note: If you don't have the permission to delete things
* Go to Edit
* Preferences
* SQL Editor
* Uncheck safe updates at the very bottom the displayed page











