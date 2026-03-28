---
title: "A3:2021 | SQL Injection  Intro (3)  | Cycubix Docs"
layout: default
nav_order: 3
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection  Intro (3)  | Cycubix Docs

As implied by the name, data manipulation language deals with the manipulation of data. Many of the most common SQL statements, including SELECT, INSERT, UPDATE, and DELETE, may be categorized as DML statements. DML statements may be used for requesting records (SELECT), adding records (INSERT), deleting records (DELETE), and modifying existing records (UPDATE).

If an attacker succeeds in "injecting" DML statements into a SQL database, he can violate the confidentiality (using SELECT statements), integrity (using UPDATE statements), and availability (using DELETE or UPDATE statements) of a system.

* DML commands are used for storing, retrieving, modifying, and deleting data.
* SELECT - retrieve data from a database
* INSERT - insert data into a database
* UPDATE - updates existing data within a database
* DELETE - delete records from a database
* Example:
  * Retrieve data:
  * SELECT phone\
    FROM employees\
    WHERE userid = 96134;
  * This statement retrieves the phone number of the employee who has the userid 96134.

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

Try to change the department of Tobi Barnett to 'Sales'. Note that you have been granted full administrator privileges in this assignment and can access all data without authentication.

<figure><img src="../../../../../.gitbook/assets/SQL Query 3.png" alt=""><figcaption></figcaption></figure>

**Solutio**To change the Department you need to UPDATE employees table. 

* **Update Statement:** Part of the `UPDATE` statement to modify column values in a table. You need tto modify the department. SET together with UPDATE will modify the comuns. 
* **Where condition**:  is used to filter records and extract only those that fulfill a specified condition. 

<figure><img src="../../../../../.gitbook/assets/sql solution 3.png" alt=""><figcaption></figcaption></figure>



### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
