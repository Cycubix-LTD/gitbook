---
description: If a system is vulnerable to SQL injections, aspects of that system’s CIA triad can be easily compromised. Learn how to compromise CIA with SQL string injections.
title: "A3:2021 | SQL Injection Intro (11) | Cycubix Docs"
layout: default
nav_order: 11
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (11) | Cycubix Docs

### Compromising confidentiality with String SQL injection

If a system is vulnerable to SQL injections, aspects of that system’s CIA triad can be easily compromised _(if you are unfamiliar with the CIA triad, check out the CIA triad lesson in the general category)_. In the following three lessons you will learn how to compromise each aspect of the CIA triad using techniques like _SQL string injections_ or _query chaining_.

In this lesson we will look at **confidentiality**. Confidentiality can be easily compromised by an attacker using SQL injection to read sensitive data like credit card numbers from a database.

#### What is String SQL injection? <a href="#what_is_string_sql_injection" id="what_is_string_sql_injection"></a>

If queries are built dynamically in the application by concatenating strings to it, this makes it very susceptible to String SQL injection.

\
If the input takes a string that gets inserted into a query as a string parameter, then you can easily manipulate the build query using quotation marks to form the string to your specific needs. For example, you could end the string parameter with quotation marks and input your own SQL after that.

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

You are an employee named John **Smith** working for a big company. The company has an internal system that allows all employees to see their own internal data - like the department they work in and their salary.

The system requires the employees to use a unique _authentication TAN_ to view their data.\
 

Your current TAN is **3SL99A**.

Since you always have the urge to be the most earning employee, you want to exploit the system and instead of viewing your own internal data &#x79;_&#x6F;u want to take a look at the data of all your colleagues_ to check their current salaries.

Use the form below and try to retrieve all employee data from the **employees** table. You should not need to know any specific names or TANs to get the information you need.

\
You already found out that the query performing your request looks like this:

```
"SELECT * FROM employees WHERE last_name = '" + name + "' AND auth_tan = '" + auth_tan + "';
```

#### Solution

* Insert your authentication TAN. 
* Try appending a SQL statement that always resolves to true. 0 OR 1=1.  But first we need to close the string 
* The input `' OR '1' = '1` is crafted to manipulate the SQL query. It effectively tries to break out of the intended SQL context and introduce a condition that always evaluates to true.
* Adding `--` at the end of an SQL injection payload is a technique used to comment out the rest of the SQL query. This can be used to manipulate the intended logic of the query, often to bypass security checks or authentication.

<figure><img src="../../../../../.gitbook/assets/SQL INJECTION11.png" alt=""><figcaption></figcaption></figure>



### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
