# TOPIC : TRIGGERS
## DATE: 01-04-2026
## TOOL: MySQL

---

## **WHAT IS A TRIGGER?**
A trigger is a special type of stored procedure that automatically executes when a certain event happens in a database table.
* It is automatic - you don't call it manually
* It reacts to INSERT, UPDATE, or DELETE events

---

### **WHY USE TRIGGERS?**
Triggers are usually used for:
* Maintaining data integrity
* Auditing changes (logging, inserts, updates, deletes)
* Enforcing business rules automatically

---

### **TYPES OF TRIGGERS**

| **Type** | **When it Fires** | **Example Use Case** |
| -------- | ----------------- | -------------------- |
| **BEFORE INSERT** | Before a row is inserted | Validate or modify data before insert |
| **AFTER INSERT** | After a row is inserted | Log new records in an audit table |
| **BEFORE UPDATE** | Before a row is updated | Check constraints or modify data before update |
| **AFTER UPDATE** | After a row is updated | Track changes for audit purposes |
| **BEFORE DELETE** | Before a row is deleted | Prevent deletion based on certain conditions |
| **AFTER DELETE** | After a row is deleted | Archive deleted records |

---

### **BASIC SYNTAX**
```sql
CREATE TRIGGER trigger_name
[BEFORE | AFTER ] [INSERT|UPDATE|DELETE]
ON table_name
FOR EACH ROW
BEGIN
  -- <i>sql statements here</i>
END;
```

---

### EXAMPLES
1️⃣ AFTER INSERT Trigger (Audit Logging)

```sql
CREATE TRIGGER after_order_insert
AFTER INSERT ON orders
FOR EACH ROW
BEGIN
  INSERT INTO orders_audit(customerid, orderid, action, action_time)
  VALUES (NEW.customerid, NEW.orderid, 'INSERT', NOW());
END;
```

### Explanation
* Fires after a new order is inserted
* Logs the insert into `orders_audit ` table
* `NEW` refers to the newly inserted row.

---

2️⃣ BEFORE UPDATE Trigger (Data Validation)

```sql
CREATE TRIGGER before_product_update
BEFORE UPDATE ON products
FOR EACH ROW
BEGIN
    IF NEW.price < 0 THEN
        SET NEW.price = 0;
    END IF;
END;
```
### Explanation
* Prevents negative prices before updating the `products` table
* `NEW` refers to the row after update

---

3️⃣ AFTER DELETE Trigger (Archiving)
```sql
CREATE TRIGGER after_customer_delete
AFTER DELETE ON customers
FOR EACH ROW
BEGIN
    INSERT INTO customers_archive(customerid, name, deleted_at)
    VALUES (OLD.customerid, OLD.name, NOW());
END;
```
### Explanation
* Fires after a customer is deleted
* `old` refers to the new row before deletion
* Archives deleted records for reference.

---

### **KEY POINTS TO REMEMBER**
1. Triggers are automatic - no need to call them manually
2. Use `NEW` for the row after insertion/update, `OLD` for the row before deletion/update.
3. Triggers can impact performance if overused - avoid complex computations inside triggers
4. Triggers are per row (`FOR EACH ROW`) by default, but some databases support statement-level triggers

---

### **COMMON USE CASES**
* Audit and log tracking
* Enforcing complex business rules
* Automatic updates of summary tables
* Archiving or backup of deleted/updated records.
