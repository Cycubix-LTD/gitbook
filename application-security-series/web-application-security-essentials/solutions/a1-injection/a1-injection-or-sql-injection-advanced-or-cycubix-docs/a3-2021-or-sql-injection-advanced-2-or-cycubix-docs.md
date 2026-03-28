---
title: "A3:2021 | SQL Injection Advanced (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A3:2021 | SQL Injection Advanced | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Advanced (2) | Cycubix Docs

### Special Characters <a href="#special_characters" id="special_characters"></a>

```
/* */          are inline comments
-- , #          are line comments

Example: SELECT * FROM users WHERE name = 'admin' -- AND pass = 'pass'
```

```
;        allows query chaining

Example: SELECT * FROM users; DROP TABLE users;
```

```
',+,||         allows string concatenation
Char()         strings without quotes

Example: SELECT * FROM users WHERE name = '+char(27) OR 1=1
```

### Special Statements <a href="#special_statements" id="special_statements"></a>

#### Union <a href="#union" id="union"></a>

The Union operator is used, to combine the results of two or more SELECT Statements.

Rules to keep in mind, when working with a UNION:

* The number of columns selected in each statement must be the same.
* The datatype of the first column in the first SELECT statement, must match the datatype of the first column in the second (third, fourth, …​) SELECT Statement. The Same applies to all other columns.

```
SELECT first_name FROM user_system_data UNION SELECT login_count FROM user_data;
```

The UNION ALL Syntax also allows duplicate Values.

#### Joins <a href="#joins" id="joins"></a>

The Join operator is used to combine rows from two or more tables, based on a related column

```
SELECT * FROM user_data INNER JOIN user_data_tan ON user_data.userid=user_data_tan.userid;
```

For more detailed information about JOINS visit: [https://www.w3schools.com/sql/sql\_join.asp](https://www.w3schools.com/sql/sql_join.asp)
