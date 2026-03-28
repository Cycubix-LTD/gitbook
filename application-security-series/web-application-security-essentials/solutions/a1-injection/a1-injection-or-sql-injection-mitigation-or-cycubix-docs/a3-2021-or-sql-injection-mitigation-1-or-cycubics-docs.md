---
title: "A3:2021 | SQL Injection Mitigation (1) | Cycubics Docs"
layout: default
nav_order: 1
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (1) | Cycubics Docs

### Immutable Queries <a href="#immutable_queries" id="immutable_queries"></a>

These are the best defense against SQL injection. They either do not have data that could get interpreted or they treat the data as a single entity that is bound to a column without interpretation.

### Static Queries

```
SELECT * FROM products;
```

```
SELECT * FROM users WHERE user = "'" + session.getAttribute("UserID") + "'";
```

### Parameterized Queries

```
String query = "SELECT * FROM users WHERE last_name = ?";
PreparedStatement statement = connection.prepareStatement(query);
statement.setString(1, accountName);
ResultSet results = statement.executeQuery();
```

### Stored Procedures

Only if stored procedure does not generate dynamic SQL.

### Immutable Queries <a href="#immutable_queries" id="immutable_queries"></a>

These are the best defense against SQL injection. They either do not have data that could get interpreted or they treat the data as a single entity that is bound to a column without interpretation.

### Static Queries

```
SELECT * FROM products;
```

```
SELECT * FROM users WHERE user = "'" + session.getAttribute("UserID") + "'";
```

### Parameterized Queries

```
String query = "SELECT * FROM users WHERE last_name = ?";
PreparedStatement statement = connection.prepareStatement(query);
statement.setString(1, accountName);
ResultSet results = statement.executeQuery();
```

### Stored Procedures

Only if stored procedure does not generate dynamic SQL.
