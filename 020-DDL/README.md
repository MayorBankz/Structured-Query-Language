# SQL - Data Definition Language (DDL)
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
