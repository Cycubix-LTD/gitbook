---
title: "A3:2021 | SQL Injection Intro (8) | Cycubix Docs"
layout: default
nav_order: 8
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (8) | Cycubix Docs

### Severity of SQL injection <a href="#severity_of_sql_injection" id="severity_of_sql_injection"></a>

#### The severity of SQL injection attacks is limited by: <a href="#the_severity_of_sql_injection_attacks_is_limited_by" id="the_severity_of_sql_injection_attacks_is_limited_by"></a>

* Attacker’s skill and imagination.
* Defense in depth countermeasures.
  * Input validation.
  * Least privilege.
* Database technology.

#### Not all databases support command chaining: <a href="#not_all_databases_support_command_chaining" id="not_all_databases_support_command_chaining"></a>

* Microsoft Access.
* MySQL Connector/J and C
* Oracle

#### SQL injection is more common in PHP, Classic ASP, Cold Fusion and older languages: <a href="#sql_injection_is_more_common_in_php_classic_asp_cold_fusion_and_older_languages" id="sql_injection_is_more_common_in_php_classic_asp_cold_fusion_and_older_languages"></a>

* Languages that do not provide parameterized query support.
* Parameterized queries have been added to newer versions.
* Early adopters of web technology (i.e. Old Code).

#### Not all databases are equal (SQL Server): <a href="#not_all_databases_are_equal_sql_server" id="not_all_databases_are_equal_sql_server"></a>

* Command shell: `master.dbo.xp_cmdshell 'cmd.exe dir c:'`
* Registry commands: `xp_regread`, `xp_regdeletekey`, …
