# SQL - Data Definition Language (DDL) & Data Manipulation Language (DML)
## TOOL - MySQL
## DATE - 27-01-2026

---

### DATA DEFINITION LANGUAGE

DDL is a part of SQL used to create, change, and delete database structures (not the data inside them).

👉 Think of DDL as the blueprint tools of a database.

---

### COMMON DDL COMMANDS

1. `CREATE` - Creates database objects

```sql
CREATE TABLE persons (
    id INT NOT NULL,
    person_name VARCHAR(50) NOT NULL,
    birth_date DATE,
    phone VARCHAR(15) NOT NULL,
    CONSTRAINT pk_persons PRIMARY KEY(id)
);
```

---

2. `ALTER` - Modifies existing objects

```sql
ALTER TABLE persons
    ADD email VARCHAR(50) NOT NULL
```

```sql
ALTER TABLE persons
    DROP COLUMN phone
```

3. `DROP` - deletes objects completely

```sql
DROP TABLE persons
```

4. `TRUNCATE` - Removes all records but keeps the table

```sql
TRUNCATE TABLE customers;
```

5. `RENAME` - changes object name

```sql

RENAME TABLE persons TO customers;

```

---

### KEY POINTS TO REMEMBER
* Affect structure, not individual rows
* Changes are usually permanent (auto-commit)
* Used by DBAs and developers

---

## DATA MANIPULATION LANGUAGE

DML is a part of SQL used to add, change, retrieve, and delete data inside database tables.

👉 Think of DML as working with the data itself, not the table structure.

---
### 🔑 Common DML Commands

1. `INSERT` - Adds new date


```sql
INSERT INTO table_name (column1, column2, column3,....)
VALUES (Value1, Value2, Value3,.....)
```

NOTE: The number of columns and values must match.

2. INSERT using SELECT

```sql
INSERT INTO table_name (column1, column2, column3,....)
SELECT column1, column2, column3
FROM table
```

3. UPDATE - Modifies exisiting data
```sql
UPDATE table_name
SET column1 = Value1,
    column2 = Value2
WHERE <condition>
```

NOTE: Always use WHERE to avoid UPDATING all roows unintentionally

4. DELETE - remomves data

```sql
DELETE FROM table_name
WHERE <condition>
```

NOTE: Always use WHERE to avoid DELETING all rows unintentionally.

---

### KEY POINTS TO REMEMBER
* Affects data, not structure
* Used in day-to-day database operations.

