---
title: "A3:2021 | SQL Injection Mitigation (2) |"
layout: default
nav_order: 2
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (2) |

### Stored Procedures <a href="#stored_procedures" id="stored_procedures"></a>

Stored procedures in SQL are a set of SQL statements stored in the database, executed as a single unit. They encapsulate and reuse code, enforce business logic, and enhance performance by reducing data exchange between the database and the application.

#### Safe Stored Procedure (Microsoft SQL Server) <a href="#safe_stored_procedure_microsoft_sql_server" id="safe_stored_procedure_microsoft_sql_server"></a>

```
CREATE PROCEDURE ListCustomers(@Country nvarchar(30))
AS
SELECT city, COUNT(*)
FROM customers
WHERE country LIKE @Country GROUP BY city


EXEC ListCustomers ‘USA’
```

#### Injectable Stored Procedure (Microsoft SQL Server) <a href="#injectable_stored_procedure_microsoft_sql_server" id="injectable_stored_procedure_microsoft_sql_server"></a>

```
CREATE PROCEDURE getUser(@lastName nvarchar(25))
AS
declare @sql nvarchar(255)
set @sql = 'SELECT * FROM users WHERE
            lastname = + @LastName + '
exec sp_executesql @sql
```

### Stored Procedures in SQL <a href="#stored_procedures" id="stored_procedures"></a>

#### Stored Procedures in SQL

Stored procedures in SQL consist of one or more SQL statements stored in the database. Executable as a single unit, they encapsulate code, enforce business logic, and boost performance by minimizing data transfer between the database and the application.

#### Safe Stored Procedure (Microsoft SQL Server) <a href="#safe_stored_procedure_microsoft_sql_server" id="safe_stored_procedure_microsoft_sql_server"></a>

```
CREATE PROCEDURE ListCustomers(@Country nvarchar(30))
AS
SELECT city, COUNT(*)
FROM customers
WHERE country LIKE @Country GROUP BY city


EXEC ListCustomers ‘USA’
```

#### Injectable Stored Procedure (Microsoft SQL Server) <a href="#injectable_stored_procedure_microsoft_sql_server" id="injectable_stored_procedure_microsoft_sql_server"></a>

```
CREATE PROCEDURE getUser(@lastName nvarchar(25))
AS
declare @sql nvarchar(255)
set @sql = 'SELECT * FROM users WHERE
            lastname = + @LastName + '
exec sp_executesql @sql
```
