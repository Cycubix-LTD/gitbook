---
title: "A3:2021 | SQL Injection Advanced (6)| Cycubix Docs"
layout: default
nav_order: 6
parent: "A3:2021 | SQL Injection Advanced | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Advanced (6)| Cycubix Docs



Now it is time for a quiz! It is recommended to do all SQL injection lessons before trying the quiz. Answer all questions correctly to complete the assignment.

**1. What is the difference between a prepared statement and a statement?**

<mark style="color:green;">Option 4: A statement has got values instead of a prepared statement</mark>

**2. Which one of the following characters is a placeholder for variables?**

Option 3: 

**3. How can prepared statements be faster than statements?**

<mark style="color:green;">Option 2: Prepared statements are compiled once by the database management system waiting for input and are pre-compiled this way.</mark>

**4. How can a prepared statement prevent SQL-Injection?**

<mark style="color:green;">Option 3: Placeholders can prevent that the users input gets attached to the SQL query resulting in a seperation of code and data.</mark>

**5. What happens if a person with malicious intent writes into a register form :Robert); DROP TABLE Students;-- that has a prepared statement?**

<mark style="color:green;">Option 4: The database registers 'Robert' ); DROP TABLE Students;--'.</mark>
