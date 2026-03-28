---
description: Data control language is used to create privileges to allow users to access and manipulate the database. Learn more about Data Control Language (DCL) now
title: "A3:2021 | SQL Injection Intro (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (5) | Cycubix Docs



#### Data Control Language (DCL) <a href="#data_control_language_dcl" id="data_control_language_dcl"></a>

Data control language is used to implement access control logic in a database. 

DCL can be used to revoke and grant user privileges on database objects such as tables, views, and functions.

If an attacker successfully "injects" DCL type SQL commands into a database, he can violate the confidentiality (using GRANT commands) and availability (using REVOKE commands) of a system. For example, the attacker could grant himself admin privileges on the database or revoke the privileges of the true administrator.

* DCL commands are used to implement access control on database objects.
* GRANT - give a user access privileges on database objects
* REVOKE - withdraw user privileges that were previously given using GRANT

Try to grant rights to the table `grant_rights` to user `unauthorized_user`:

#### Solution

* The `GRANT ALL ON` command in SQL is used to give all privileges on a specific database object (such as a table, database, or view) to a user or role. This command is part of the Data Control Language (DCL) and is used to manage access control in a database syste

<figure><img src="../../../../../.gitbook/assets/sql grant on.png" alt=""><figcaption></figcaption></figure>

### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
