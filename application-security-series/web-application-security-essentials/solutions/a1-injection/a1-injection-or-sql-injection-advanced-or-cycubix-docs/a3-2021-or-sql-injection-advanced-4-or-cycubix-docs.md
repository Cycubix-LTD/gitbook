---
title: "A3:2021 | SQL Injection Advanced (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A3:2021 | SQL Injection Advanced | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Advanced (4) | Cycubix Docs

### Blind SQL injection <a href="#blind_sql_injection" id="blind_sql_injection"></a>

Blind SQL injection is a type of SQL injection attack that asks the database true or false questions and determines the answer based on the application’s response. This attack is often used when the web application is configured to show generic error messages, but has not mitigated the code that is vulnerable to SQL injection.

#### Difference <a href="#difference" id="difference"></a>

Let us first start with the difference between a normal SQL injection and a blind SQL injection. In a normal SQL injection the error messages from the database are displayed and gives enough information to find out how the query is working. Or in the case of a UNION based SQL injection the application does not reflect the information directly on the web page. So in the case where nothing is displayed you will need to start asking the database questions based on a true or false statement. That is why a blind SQL injection is much more difficult to exploit.

There are several different types of blind SQL injections: content-based and time-based SQL injections.

#### Example <a href="#example" id="example"></a>

In this case we are trying to ask the database a boolean question based on a unique id, for example suppose we have the following url: [`https://my-shop.com?article=4`](https://my-shop.com/?article=4) On the server side this query will be translated as follows:

```
SELECT * FROM articles WHERE article_id = 4
```

When we want to exploit this we change the url into: [`https://shop.example.com?article=4`](https://shop.example.com/?article=4) `AND 1=1` This will be translated to:

```
SELECT * FROM articles WHERE article_id = 4 and 1 = 1
```

\
If the browser will return the same page as it used to when using [`https://shop.example.com?article=4`](https://shop.example.com/?article=4) you know the website is vulnerable for a blind SQL injection. If the browser responds with a page not found or something else you know a blind SQL injection might not work. You can now change the SQL query and test for example: [`https://shop.example.com?article=4`](https://shop.example.com/?article=4) `AND 1=2` which will not return anything because the query returns false.
