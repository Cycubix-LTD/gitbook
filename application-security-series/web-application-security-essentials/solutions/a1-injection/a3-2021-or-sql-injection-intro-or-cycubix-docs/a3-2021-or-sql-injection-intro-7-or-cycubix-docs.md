---
title: "A3:2021 | SQL Injection Intro (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (7) | Cycubix Docs

### Consequences of SQL injection <a href="#consequences_of_sql_injection" id="consequences_of_sql_injection"></a>

#### A successful SQL injection exploit can: <a href="#a_successful_sql_injection_exploit_can" id="a_successful_sql_injection_exploit_can"></a>

* Read and modify sensitive data from the database
* Execute administrative operations on the database
  * Shutdown auditing or the DBMS
  * Truncate tables and logs
  * Add users
* Recover the content of a given file present on the DBMS file system
* Issue commands to the operating system

#### SQL injection attacks allow attackers to <a href="#sql_injection_attacks_allow_attackers_to" id="sql_injection_attacks_allow_attackers_to"></a>

* Spoof identity
* Tamper with existing data
* Cause repudiation issues such as voiding transactions or changing balances
* Allow the complete disclosure of all data on the system
* Destroy the data or make it otherwise unavailable
* Become administrator of the database server
