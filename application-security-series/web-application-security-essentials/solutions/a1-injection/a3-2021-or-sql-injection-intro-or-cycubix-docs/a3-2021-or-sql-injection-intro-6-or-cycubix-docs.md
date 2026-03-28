---
title: "A3:2021 | SQL Injection Intro (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (6) | Cycubix Docs

### What is SQL injection? <a href="#what_is_sql_injection" id="what_is_sql_injection"></a>

SQL injection (also called SQLi) is one of the most common web hacking techniques. **A SQL injection attack consists of insertion or "injection" of malicious code via the SQL query input from the client to the application.** If not dealt with correctly, SQL injection can seriously impact data integrity and security.

SQL injections can occur when unfiltered data from the client, such as input from a search field, gets into the SQL interpreter of the application itself. If an application fails to either correctly sanitize user input (using prepared statements or similar) or filter the input against special characters, hackers can manipulate the underlying SQL statement to their advantage.\
For example, if the input is not filtered for SQL metacharacters like **--** (which comments out the rest of the line) or **;** (which ends a SQL query), SQL injection may result.

### Example of SQL injection <a href="#example_of_sql_injection" id="example_of_sql_injection"></a>

For example, consider a web application that allows users to retrieve user information simply by inputting a username into a form field. The input from the user is sent to the server and gets inserted into a SQL query which then is processed by a SQL interpreter.

The SQL query to retrieve the user information from the database follows:<br>

```
"SELECT * FROM users WHERE name = '" + userName + "'";
```

The variable **userName** holds the input from the client and “injects” it into the query.<br>

If the input were Smith the query would then become:<br>

```
"SELECT * FROM users WHERE name = 'Smith'";
```

and would retrieve all data for the user with the name Smith.

If an attacker inputs data containing **characters or strings that have a "special"** (find more information at the button of this page) meaning to the SQL interpreter (such as **;**, **--**, or **'**), and the data is not correctly sanitized or validated, the attacker can modify the intended behavior of the SQL query in order to perform other (malicious) actions on the database.

Here is an input field. Try typing some SQL in here to better understand how the query changes.

```
"SELECT * FROM users WHERE name = ''";
```



<figure><img src="../../../../../.gitbook/assets/typing SQL query changes.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

SQL injection can be used for far more than reading the data of a single of user. The following are just a few examples of data a hacker could input to a form field (or anywhere user input is accepted) in an attempt to exploit a SQL injection vulnerability:

* `Smith' OR '1' = '1`\
  results in `SELECT * FROM users WHERE name = 'Smith' OR TRUE;` which will return all entries from the users table
* `Smith' OR 1 = 1; --`\
  results in `SELECT * FROM users WHERE name = 'Smith' OR TRUE;--';` which, like the first example, will also return all entries from the users table
* `Smith'; DROP TABLE users; TRUNCATE audit_log; --`\
  chains multiple SQL-Commands in order to both DROP the users table and delete all entries from the audit\_log table. 



#### Special Characters in SQL

1. **Single Quote (`'`)**
   * Used to enclose string literals.
   * Example: `'John Doe'`
   * Used for escaping single quotes within strings: `''`
2. **Double Quote (`"`)**
   * Used to enclose identifiers (e.g., column and table names) in some SQL databases.
   * Example: `"column_name"`
3. **Backtick (\`\`\`)**
   * Used to enclose identifiers in MySQL.
   * Example: `` `table_name` ``
4. **Semicolon (`;`)**
   * Used to terminate SQL statements.
   * Example: `SELECT * FROM employees;`
5. **Asterisk (`*`)**
   * Used as a wildcard character to select all columns.
   * Example: `SELECT * FROM employees;`
6. **Percent Sign (`%`)**
   * Used as a wildcard character in the `LIKE` operator to match zero or more characters.
   * Example: `SELECT * FROM employees WHERE name LIKE 'J%';`
7. **Underscore (`_`)**
   * Used as a wildcard character in the `LIKE` operator to match a single character.
   * Example: `SELECT * FROM employees WHERE name LIKE 'J_n';`
8. **Parentheses (`()`)**
   * Used to group expressions, enclose subqueries, and define function parameters.
   * Example: `SELECT (salary + bonus) FROM employees;`
   * Example: `SELECT * FROM (SELECT * FROM employees) AS subquery;`
9. **Comma (`,`)**
   * Used to separate columns in a `SELECT` statement or values in an `INSERT` statement.
   * Example: `SELECT id, name, salary FROM employees;`
   * Example: `INSERT INTO employees (id, name, salary) VALUES (1, 'John Doe', 50000);`
10. **Equal Sign (`=`)**
    * Used as an equality operator in `WHERE` clauses.
    * Example: `SELECT * FROM employees WHERE id = 1;`
11. **Less Than (`<`), Greater Than (`>`), Less Than or Equal To (`<=`), Greater Than or Equal To (`>=`)**
    * Used as comparison operators.
    * Example: `SELECT * FROM employees WHERE salary > 50000;`
12. **Exclamation Mark and Equal (`!=` or `<>`)**
    * Used as inequality operators.
    * Example: `SELECT * FROM employees WHERE department != 'Sales';`
13. **Ampersand (`&`), Vertical Bar (`|`), Tilde (`~`), Caret (`^`)**
    * Used as bitwise operators in some SQL dialects.
    * Example: `SELECT 5 & 3;` (Bitwise AND)
14. **Plus (`+`), Minus (`-`), Asterisk (`*`), Slash (`/`)**
    * Used as arithmetic operators.
    * Example: `SELECT salary + bonus FROM employees;`
    * Example: `SELECT salary / 2 FROM employees;`
15. **Double Dash (`--`)**
    * Used to indicate a single-line comment.
    * Example: `-- This is a comment`
16. **Slash Asterisk (`/* ... */`)**
    * Used to indicate a multi-line comment.
    * Example: `/* This is a multi-line comment */`

