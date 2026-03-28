---
title: "A3:2021 | SQL Injection Intro (9) | Cycubix Docs"
layout: default
nav_order: 9
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (9) | Cycubix Docs

The query in the code builds a dynamic query as seen in the previous example. The query is built by concatenating strings making it susceptible to String SQL injection: Try It! String SQL injection.

```
"SELECT * FROM user_data WHERE first_name = 'John' AND last_name = '" + lastName + "'";
```

Using the form below try to retrieve all the users from the users' table. You should not need to know any specific user name to get the complete list.

<figure><img src="../../../../../.gitbook/assets/sql injection 9 1.png" alt=""><figcaption></figcaption></figure>

#### Solution

* Hint:  Remember that for an successful Sql-Injection the query needs to always evaluate to true.

**SELECT \* FROM users\_data FIRST\_NAME = 'John' and Last\_NAME = '** `'` + `or` + `'1'='1`

<figure><img src="../../../../../.gitbook/assets/SQL injection 9 2.png" alt=""><figcaption></figcaption></figure>

In the context of SQL injection, "**evaluating truth**" refers to a technique where an attacker exploits the way SQL queries evaluate conditions to manipulate the query's execution and achieve unauthorized actions or access. This technique often involves inserting or modifying parts of an SQL query to make conditions always evaluate to true, thus bypassing authentication or filtering mechanisms.

### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).

