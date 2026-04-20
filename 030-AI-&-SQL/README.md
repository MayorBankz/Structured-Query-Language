## TOPIC: AI & SQL (How to use AI for SQL Effectively)
## DATE: 17-04-26
## TOOL: MySQL, CHATGPT, DEEPSEEK, GITHUB COPILOT

---

### **WHAT IS AI IN SQL**
AI in SQL refers to using tools like ChatGPT, GitHub Copilot, or database-integrated AI features to write, optimize, explain, and debug SQL queries automatically.
Instead of manually crafting queries, you describe what you want in plain English, and AI translates it into SQL.

---

### **SIMPLE ANALOGY**
Think of SQL as a language for talking to databases, and AI as a translator.
* You say "_Give me top customers by revenue last month_"
* AI converts it into:
```sql
SELECT customer_id, SUM(revenue)
FROM orders
WHERE order_date >= '2026-03-01'
GROUP BY customer_id
ORDER BY SUM(revenue) DESC;
```

---

### **WHY USE AI FOR SQL?**
a. **Speed**
AI reduces query writing time from minutes to seconds.
b. **Learning Boost**
You understand advanced concepts faster (window functions, CTEs, joins).
c. **Error reduction**
AI helps catch:
* Syntax errors
* Logic mistakes
* Missing conditions
d. **Productivity**
You focus more on analysis instead of syntax

---

### **WHEN SHOULD YOU USE AI**
Use AI when:
* You're stuck on a query
* You need optimization
* You want explanations
* You're exploring new SQL concepts
* You need quick insights from data
Avoid relying blindly when:
* You don't understand the output
* Data accuracy is critical (always validate)

---

### **WHEN TO USE AI FOR SQL**

### 🔷 **Solve an SQL Task**

#### _PROMPT_

In my SQL server database, we have two tables:
The first table is `Orders` with the following `Columns`: `Order_id`, `sales`, `customer_id`, `product_id`.
The second table is `customers` with the following columns: `customer_id`, `first_name`, `last_name`, `country`.
Do the following:
* Write a wuery to rank customers based on their sales
* The result should include the customer's customer_id, full_name, country, total_sales, and their rank.
* Include comments but avoid commenting on obvious parts
* Write three different versions of the query to achieve this task.
* Evaluate and explain which is version is best in terms of readability and performance.

---

### 🔷 **Improve the Readability**

#### _PROMPT_

The following SQL server query is long and hard to understand
Do the following:
* Improve it's readability.
* Remove any redundancy in the query and consolidate it.
* Include comments but avoid commenting on obvious parts
* Explain each improvement to understand the reasoning behind it.

---

### 🔷 **Optimize the performance query**

#### _PROMPT_

The following SQL server query is slow.
Do the following:
* Propose optimization to improve it's performance
* Provide the improved SQL query
* Explain each improvement to understand the reasoning behind it.

---

### 🔷 **Optimize Execution Plan**

#### _PROMPT_
The _image_ is the execution plan of SQL server query.
Do the following:
* Describe the execution plan step by step 
* Identify performance bottlenecks and issues
* Suggest ways to improve performance and optimize the execution plan
* Ensure the formatting follows best practices
[SQL Query Goes Here]

---

### 🔷 **Debugging**

#### _PROMPT_

The following SQL server query causing this error: [Error Message Goes Here]
Do the following:
* Explain the error message
* Find the root cause of the issue
* Suggest how to fix it
[SQL Query Goes Here]

---

### 🔷 **Explain the Result**

#### _PROMPT_

I didn't understand the result of the following SQL server query
Do the following:
* Break down how SQL processes the following query step by step explaining each stage and how the result is formed.
[SQL Query Goes Here]

---

### 🔷 **Styling & Formatting**

#### _PROMPT_

The following SQL server query is hard to understand 
Do the following:
* Restyle the code to make it easier to read
* Align column aliases
* Keep it compact - do not introduce unnecessary new lines
* Ensure the formatting follows best practices.
[SQL Query Goes Here]

---

### 🔷 **Documentations & Comments**

#### _PROMPT_

The following SQL server query lacks comments and documentations 
Do the following
* Insert a leading comment at the start of the query describing its overall purpose
* Add comments only where clarification is necessary, avoiding obvious statements
* Create a separate document explaining the business rules implemented by the query
* Create another separate document describing how the query works
[SQL Query Goes Here]

---

### 🔷 **Improve Database DDL**

#### _PROMPT_

The following SQL server DDL script has to be optimized.
Do the following
* Naming - Check the consistency of table/column names, prefixes, standards.
* Data Types - Ensure data types are appropriate and optimized.
* Integrity - Verify the integrity of primary keys and foreign keys.
* Indexes - Check that indexes are sufficient and avoid redundancy.
* Normalization - Ensure proper normalization and avoid redundancy

---

### 🔷 **Generate Test Dataset**

#### _PROMPT_

I need dataset for testing the following SQL server DDL
Do the following:
* Generate test dataset as insert statements
* Dataset should be realistic
* Keep the dataset small
* Ensure all primary/foreign key relationships are valid (Use matching IDs).
* Don't introduce any NULL values.
[SQL DDL Goes Here]

---

### 🔷 **Create SQL Course (For Students)**

#### _PROMPT_

Create a comprehensive SQL course with a detailed roadmap and agenda.
Do the following:
* Start with SQL fundamentals and advance to complex topics.
* Make it beginner-friendly
* Include topics relevant to data analytics
* Focus on real-world data analytics use cases and scenarios

---

### 🔷 **Understanding SQL Concepts**

#### _PROMPT_

I want detailed explanation about SQL Window Functions
Do the following:
* Explain what Window Functions are
* Give an analogy
* Describe why we need them and when to use them.
* Explain the syntax
* Provide simple examples
* List the top 3 use cases

---

### 🔷 **Comparing SQL Concepts**

#### _PROMPT_

I want to understand THE differences between SQL WINDOWS and GROUP BY 
Do the following:
* Explain the key differences between the two concepts
* Describe when to use each concepts with examples
* Provide the pros & cons of each concept
* Summarize the coomparison in a clear side-by-side table.

---

### 🔷 **Practice SQL**

#### _PROMPT_

Act as an SQL trainer and help me practice SQL Window Functions
Do the following:
* Make it interactive practicing, you provide tasks and I give solutions
* Provide a simple dataset
* Give SQL tasks that gradually increases in difficulty
* Act as an SQL server and show the result of my queries
* Review my queries, provide feedback, and suggest improvements.

--- 

### 🔷 **Prepare for an SQL interview**

#### _PROMPT_

Act as an interviewer and prepare me for an SQL interview
Do the following:
* Ask common SQL interview questions
* Make it interactive practicing, you provide questions and I give answer.
* Gradually progress to advanced topics
* Evaluate my answer and give me a feedback
