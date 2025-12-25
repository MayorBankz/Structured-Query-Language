# SQL - STRING FUNCTIONS
## DATE - 16-12-25
## TOOL - MySQL

## SQL String Functions Documentation

### Character Manipulation Funtion 
String functions in SQL are used to manipulate and analyze text (character data). They help you format, search, extract, and combine strings in a database.

i). Length - Returns the number of characters in a string.

### SYNTAX
```sql
LENGTH(string)
```
### Example

```sql
SELECT LENGTH('Database');
```
`Output:` 8

ii). UPPER - Converts all characters in a string to uppercase.

### SYNTAX

UPPER(string)

### Example
```sql
SELECT UPPER('sql functions');
```
`Output:` SQL FUNCTIONS

iii). LOWER - Converts all characters in a string to lowercase.

### SYNTAX

LOWER(string)

### Example
```sql
SELECT LOWER('HELLO WORLD');
```
`Output:` hello world

iv). TRIM (LEFT & RIGHT) - Removes unwanted spaces from a string.

* TRIM → removes spaces from both sides
* LTRIM → removes spaces from the left
* RTRIM → removes spaces from the right

### SYNTAX
```sql
TRIM(string)
LTRIM(string)
RTRIM(string)
```

### Example 
```sql
SELECT TRIM('   SQL   ');
```
`Output:` SQL

v). LEFT - Extracts a specified number of characters from the left side of a string.

### SYNTAX
```sql
LEFT(string, number)
```

### Example 
```sql
SELECT LEFT('Database', 4);
```

vi) RIGHT - Extracts a specified number of characters from the right side of a string.

### SYNTAX 
```sql
RIGHT(string, number)
```

### Example 
```sql
SELECT RIGHT('Database', 4);
```
`Output:` base

vii) SUBSTRING - Extracts part of a string starting from a given position.

### SYNTAX
```sql
SUBSTRING(string, start, length)
```

### Example
```sql
SELECT SUBSTRING('Database', 2, 4);
```
`Output:` atab

viii). REPLACE - Replaces all occurrences of a substring with another substring.

### SYNTAX
```sql
REPLACE(string, old_value, new_value)
```

### Example 
```sql
SELECT REPLACE('I love SQL', 'SQL', 'Databases');
```
`Output:` I love Databases

ix). LOCATE - Finds the position of a substring within a string.

### SYNTAX
```sql
LOCATE(substring, string)
```

### Example
```sql
SELECT LOCATE('SQL', 'I love SQL');
```
`Output:` 8

x). CONCAT - Combines two or more strings into one.

### SYNTAX
```sql
CONCAT(string1, string2, ...)
```
### Example
```sql
SELECT CONCAT('Hello', ' ', 'World');
```
`Output:` Hello World

## SUMMARY 

SQL string functions are essential for:

* Formatting text
* Cleaning data
* Extracting useful information
* Searching with strings


## Practical Examples

* Length

<img width="589" height="695" alt="image" src="https://github.com/user-attachments/assets/4c15868a-9b42-4c3e-8ed0-b970d552fba9" />

* UPPER

<img width="718" height="726" alt="image" src="https://github.com/user-attachments/assets/5142a371-08e0-4881-b214-57c306c38428" />

* lower

<img width="850" height="720" alt="image" src="https://github.com/user-attachments/assets/ec8881e5-72d2-420f-8c42-4e13fd2f34fb" />

* TRIM

<img width="737" height="557" alt="image" src="https://github.com/user-attachments/assets/ce17b15f-4b72-4665-8b7d-54c336d463fd" />

* LTRIM

<img width="854" height="565" alt="image" src="https://github.com/user-attachments/assets/b229b63d-8d03-4059-adcc-d0f3e6e6ef21" />

* RTRIM

<img width="905" height="556" alt="image" src="https://github.com/user-attachments/assets/c6666fe0-e967-4d80-b72b-dec170883519" />

* LEFT

<img width="860" height="748" alt="image" src="https://github.com/user-attachments/assets/0ff50d01-c555-4f1f-86b1-1571e2651f8e" />

* RIGHT

<img width="850" height="773" alt="image" src="https://github.com/user-attachments/assets/2776b399-19a5-41ec-9e97-e6e6ee5186ca" />

* SUBSTRING

<img width="864" height="713" alt="image" src="https://github.com/user-attachments/assets/e1d8e95d-c078-4bd7-9bc7-103f7d0d5185" />

* REPLACE

<img width="980" height="735" alt="image" src="https://github.com/user-attachments/assets/468acd45-949b-4089-a680-097c0c365f46" />

* LOCATE

<img width="917" height="665" alt="image" src="https://github.com/user-attachments/assets/8969849f-f80b-4e88-a880-e0cc5e3f1b2a" />

<img width="991" height="730" alt="image" src="https://github.com/user-attachments/assets/2af7c3a9-f290-4610-8136-dff0a7c591fe" />

* CONCAT

<img width="1046" height="723" alt="image" src="https://github.com/user-attachments/assets/d5281802-2fdd-4819-90a4-f1f855a5a1cd" />
