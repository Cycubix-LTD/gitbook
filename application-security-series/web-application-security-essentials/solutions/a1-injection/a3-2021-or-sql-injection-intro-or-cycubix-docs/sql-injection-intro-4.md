---
description: Data definition language includes commands for defining data structures, especially database schemas which tell how the data should reside in the database. Read on!
title: "A3:2021 | SQL injection Intro (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL injection Intro (4) | Cycubix Docs

#### Data Definition Language (DDL) <a href="#data_definition_language_ddl" id="data_definition_language_ddl"></a>

Data definition language includes commands for defining data structures. DDL commands are commonly used to define a database’s schema. 

The schema refers to the overall structure or organization of the database and. in SQL databases, includes objects such as tables, indexes, views, relationships, triggers, and more.

If an attacker successfully "injects" DDL type SQL commands into a database, he can violate the integrity (using ALTER and DROP statements) and availability (using DROP statements) of a system.

* DDL commands are used for creating, modifying, and dropping the structure of database objects.
* CREATE - create database objects such as tables and views.
* ALTER - alters the structure of the existing database.
* DROP - delete objects from the database.
*   Example:

    * CREATE TABLE employees (

        userid varchar(6) not null primary key,\
        first\_name varchar(20),\
        last\_name varchar(20),\
        department varchar(20),\
        salary varchar(10),\
        auth\_tan varchar(6)\
    );

    * This statement creates the employees example table given on page 2.

Now try to modify the schema by adding the column "phone" (\*varchar(20)) <br>

<figure><img src="../../../../../.gitbook/assets/ddl 1.png" alt=""><figcaption></figcaption></figure>

\* Varchar is  is a data type in SQL (Structured Query Language) that stands for "variable character." It is used to store variable-length strings of characters, such as text, numbers, symbols, or a combination of these. The `VARCHAR` data type is particularly useful when the length of the data stored in the field can vary from row to row.

#### Solution

* We need to ALTER the structure of the current database. 
*  We also need to ADD a column name data type (size),

**SQL query**: `ALTER TABLE employees ADD phone varchar(20)`

<figure><img src="../../../../../.gitbook/assets/ddl solution.png" alt=""><figcaption></figcaption></figure>



### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
