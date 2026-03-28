---
title: "A3:2021 | SQL Injection Mitigation (11) | Cycubix Docs"
layout: default
nav_order: 11
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (11) | Cycubix Docs

### Order by clause <a href="#order_by_clause" id="order_by_clause"></a>

Question: Does a prepared statement always prevent against an SQL injection? Answer: No it does not

Let us take a look at the following statement:

```
"SELECT * FROM users ORDER BY " + sortColumName + ";"
```

If we look at the specification of the SQL grammar the definition is as follows:

```
SELECT ...
FROM tableList
[WHERE Expression]
[ORDER BY orderExpression [, ...]]

orderExpression:
{ columnNr | columnAlias | selectExpression }
    [ASC | DESC]

selectExpression:
{ Expression | COUNT(*) | {
    COUNT | MIN | MAX | SUM | AVG | SOME | EVERY |
    VAR_POP | VAR_SAMP | STDDEV_POP | STDDEV_SAMP
} ([ALL | DISTINCT][2]] Expression) } [[AS] label]

Based on HSQLDB
```

This means an `orderExpression` can be a `selectExpression` which can be a function as well, so for example with a `case` statement we might be able to ask the database some questions, like:

```
SELECT * FROM users ORDER BY (CASE WHEN (TRUE) THEN lastname ELSE firstname)
```

So we can substitute any kind of boolean operation in the `when(…​.)` part. The statement will just work because it is a valid query whether you use a prepared statement or not. An order by clause can by definition contain an expression.

#### Mitigation <a href="#mitigation" id="mitigation"></a>

If you need to provide a sorting column in your web application you should implement a whitelist to validate the value of the `order by` statement. It should always be limited to something like 'first name' or 'last name'.
