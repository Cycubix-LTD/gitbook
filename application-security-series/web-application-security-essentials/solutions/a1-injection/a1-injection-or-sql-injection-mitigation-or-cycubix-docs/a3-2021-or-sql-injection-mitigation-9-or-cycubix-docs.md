---
title: "A3:2021 | SQL Injection Mitigation (9) | Cycubix Docs"
layout: default
nav_order: 9
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (9) | Cycubix Docs

### Input validation alone is not enough!! <a href="#input_validation_alone_is_not_enough" id="input_validation_alone_is_not_enough"></a>

You need to do both, use parametrized queries and validate the input received from the user. On StackOverflow you will see a lot of answers stating that input validation is enough. **However** it only takes you so far before you know the validation is broken, and you have an SQL injection in your application.

The link provided by WebGoat has expired, for more information we recommend this article: [invicti.com](https://www.invicti.com/blog/web-security/input-validation-errors-root-of-all-evil/)

Let’s repeat one of the previous assignments, the developer fixed the possible SQL injection with filtering, can you spot the weakness in this approach?

Read about the lesson goal in SQL Injection Advanced (3). 

<figure><img src="../../../../../.gitbook/assets/sql mitigation 9.png" alt=""><figcaption></figcaption></figure>

**Solution**

* We need to get retrieve all data from the `user_system_data` table. 
* Here are some of the hints: 

Spaces are rejected, try to find a way around this restriction. 

Try to use a comment in the query

WebGoat uses HSQLDB as a database can you use one of them to make skip the filtering?

* So we need to obfuscate the querie and bypass filters. 
* The code is "a';/**/select/**/\*/**/from/**/user\_system\_data;--". Let's break it down: 

`/**/`: Comment blocks are used to bypass basic filters that might look for spaces.

To retrieve all data from the `user_system_data` table while avoiding detection by basic filtering mechanisms, you can obfuscate the `SELECT` statement using comments. 

`;--`: The semicolon ends the current query, and the `--` comments out the rest of the SQL query. 

<figure><img src="../../../../../.gitbook/assets/imput validation.png" alt=""><figcaption></figcaption></figure>
