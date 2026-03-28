---
title: "A3:2021 | SQL Injection Mitigation (8) | Cycubix Docs"
layout: default
nav_order: 8
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (8) | Cycubix Docs

### Input Validation Required? <a href="#input_validation_required" id="input_validation_required"></a>

#### Since my queries are no longer injectable do I still need to validate my input? <a href="#since_my_queries_are_no_longer_injectable_do_i_still_need_to_validate_my_input" id="since_my_queries_are_no_longer_injectable_do_i_still_need_to_validate_my_input"></a>

* **YES!**

#### Prevents other types of attacks from being stored in the database <a href="#prevents_other_types_of_attacks_from_being_stored_in_the_database" id="prevents_other_types_of_attacks_from_being_stored_in_the_database"></a>

* Stored XSS.
* Information leakage.
* Logic errors - business rule validation.
* SQL injection.

#### Often the database is considered trusted <a href="#often_the_database_is_considered_trusted" id="often_the_database_is_considered_trusted"></a>
