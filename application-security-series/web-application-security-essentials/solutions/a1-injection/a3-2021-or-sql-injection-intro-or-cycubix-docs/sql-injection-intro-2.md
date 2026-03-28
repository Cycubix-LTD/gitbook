---
description: SQL is a standardized programming language which is used for managing relational databases and performing various operations on the data in them. Find out about SQL.
title: "A3:2021 | SQL Injection Intro (2)  | Cycubix Docs"
layout: default
nav_order: 2
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (2)  | Cycubix Docs

### What is SQL? <a href="#what_is_sql" id="what_is_sql"></a>

SQL is a standardized (ANSI in 1986, ISO in 1987) programming language which is used for managing relational databases and performing various operations on the data in them.

A database is a collection of data. Data is organized into rows, columns and tables, and it is indexed to make it easier to find relevant information.

Example SQL table with employees, the name of the table is 'employees':

Employees Table

| userid | first\_name | last\_name | department  | salary  | auth\_tan |   |
| ------ | ----------- | ---------- | ----------- | ------- | --------- | - |
| 32147  | Paulina     | Travers    | Accounting  | $46.000 | P45JSI    |   |
| 89762  | Tobi        | Barnett    | Development | $77.000 | TA9LL1    |   |
| 96134  | Bob         | Franco     | Marketing   | $83.700 | LO9S2V    |   |
| 34477  | Abraham     | Holman     | Development | $50.000 | UU2ALK    |   |
| 37648  | John        | Smith      | Marketing   | $64.350 | 3SL99A    |   |

A company saves the following employee information in their databases: a unique employee number ('userid'), last name, first name, department, salary and a transaction authentication number ('auth\_tan'). Each of these pieces of information is stored in a separate column and each row represents one employee of the company.

**SQL queries** can be used to modify a database table and its index structures and add, update and delete rows of data.

There are three main categories of SQL commands:

* Data Manipulation Language (DML): 
  * **SELECT**: Retrieves data from one or more tables. For example, `SELECT * FROM employees;`
  * **INSERT**: Adds new rows of data to a table. For example, `INSERT INTO employees (id, name, age) VALUES (1, 'John Doe', 30);`
  * **UPDATE**: Modifies existing data within a table. For example, `UPDATE employees SET age = 31 WHERE id = 1;`
  * **DELETE**: Removes rows of data from a table. For example, `DELETE FROM employees WHERE id = 1;`
* Data Definition Language (DDL): 
  * **CREATE**: Creates a new table, database, index, or view. For example, `CREATE TABLE employees (id INT, name VARCHAR(100));`
  * **ALTER**: Modifies an existing database object, such as adding or deleting a column. For example, `ALTER TABLE employees ADD COLUMN age INT;`
  * **DROP**: Deletes an existing table, database, index, or view. For example, `DROP TABLE employees;`
  * **TRUNCATE**: Removes all records from a table, but not the table itself. For example, `TRUNCATE TABLE employees;`
* Data Control Language (DCL): 
  * **GRANT**: Gives a user permission to perform specific tasks. For example, `GRANT SELECT ON employees TO user1;`
  * **REVOKE**: Removes a user's permission to perform specific tasks. For example, `REVOKE SELECT ON employees FROM user1;`

Each of these command types can be used by attackers to compromise the confidentiality, integrity, and/or availability of a system. Proceed with the lesson to learn more about the SQL command types and how they relate to protections goals.

If you are still struggling with SQL and need more information or practice, you can visit [http://www.sqlcourse.com/](http://www.sqlcourse.com/) for free and interactive online training.

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

Look at the example table. Try to retrieve the department of the employee Bob Franco. Note that you have been granted full administrator privileges in this assignment and can access all data without authentication. 

<figure><img src="../../../../../.gitbook/assets/SQL image.png" alt=""><figcaption></figcaption></figure>

#### Solution

* You need to find the DEPARTMENT corresponding to the employee Bob Franco. 

**SELECT**: Retrieves data from one or more tables. For example, `SELECT * FROM employees;`

`The data base name is employees, and you know the first and last name of the employee.` 

`WHERE would be the condition in the string.` 

<figure><img src="../../../../../.gitbook/assets/Results SQL 2.png" alt=""><figcaption></figcaption></figure>

**SQL query**: `SELECT department FROM employees WHERE first_name='Bob'`

The resulting department is marketing. 

<figure><img src="../../../../../.gitbook/assets/Results SQL 2 bis.png" alt=""><figcaption></figcaption></figure>

### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
