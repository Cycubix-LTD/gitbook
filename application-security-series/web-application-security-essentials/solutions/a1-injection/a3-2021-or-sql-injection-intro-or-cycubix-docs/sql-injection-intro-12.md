---
description: After compromising the confidentiality of data we are going to compromise the integrity of data by using SQL query chaining. Learn how to use SQL query chaining.
title: "A3:2021 | SQL Injection Intro (12) | Cycubix Docs"
layout: default
nav_order: 12
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (12) | Cycubix Docs

### Compromising Integrity with Query chaining <a href="#compromising_integrity_with_query_chaining" id="compromising_integrity_with_query_chaining"></a>

#### What is SQL query chaining? <a href="#what_is_sql_query_chaining" id="what_is_sql_query_chaining"></a>

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

### Compromising Integrity with Query chaining <a href="#compromising_integrity_with_query_chaining" id="compromising_integrity_with_query_chaining"></a>

After compromising the confidentiality of data in the previous lesson, this time we are gonna compromise the **integrity** of data by using SQL **query chaining**.

If a severe enough vulnerability exists, SQL injection may be used to compromise the integrity of any data in the database. Successful SQL injection may allow an attacker to change information that he should not even be able to access.

#### What is SQL query chaining? <a href="#what_is_sql_query_chaining" id="what_is_sql_query_chaining"></a>

Query chaining is exactly what it sounds like. With query chaining, you try to append one or more queries to the end of the actual query. You can do this by using the **;** metacharacter. 

A **;** marks the end of a SQL statement; it allows one to start another query right after the initial query without the need to even start a new line.

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

You just found out that Tobi and Bob both seem to earn more money than you! Of course you cannot leave it at that.

\
Better go and _change your own salary so you are earning the most!_

Remember: Your name is John **Smith** and your current TAN is **3SL99A**.

#### Solution

* If John Smith wants a raise, he needs to chain another query to the end of the existing one. 
* For rhis we can close up a string after using a truth statement: ' OR 1=1;. The semicolon ends the statements. 
* John Smithg will have to add another statement to correct the salary situation updating the salary for all rows. Update employees set salary  = 999999
*  **Authentication TAN**: `'; UPDATE employees SET salary=99999 WHERE first_name='John`

<figure><img src="../../../../../.gitbook/assets/sql injection 12 1.png" alt=""><figcaption></figcaption></figure>
