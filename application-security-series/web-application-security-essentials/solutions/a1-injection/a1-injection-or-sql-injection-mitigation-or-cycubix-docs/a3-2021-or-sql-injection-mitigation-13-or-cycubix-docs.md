---
title: "A3:2021 | SQL Injection Mitigation (13) | Cycubix Docs"
layout: default
nav_order: 13
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (13) | Cycubix Docs

### Least Privilege <a href="#least_privilege" id="least_privilege"></a>

#### - Connect with a minimum set of privileges <a href="#connect_with_a_minimum_set_of_privileges" id="connect_with_a_minimum_set_of_privileges"></a>

* The application should connect to the database with different credentials for every trust distinction.
* Applications rarely need delete rights to a table or database.

#### - Database accounts should limit schema access. <a href="#database_accounts_should_limit_schema_access" id="database_accounts_should_limit_schema_access"></a>

#### - Define database accounts for read and read/write access. <a href="#define_database_accounts_for_read_and_readwrite_access" id="define_database_accounts_for_read_and_readwrite_access"></a>

#### - Multiple connection pools based on access. <a href="#multiple_connection_pools_based_on_access" id="multiple_connection_pools_based_on_access"></a>

* Use read only access for the authentication query.
* Use read/write access for the data modification queries.
* Use execute for access to stored procedure calls.
