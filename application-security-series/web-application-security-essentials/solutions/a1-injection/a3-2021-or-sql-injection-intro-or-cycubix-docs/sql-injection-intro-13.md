---
description: After compromising confidentiality and integrity in the previous lessons, we now are going to compromise the third element of the CIA triad availability. Read more
title: "A3:2021 | SQL Injection Intro (13) | Cycubix Docs"
layout: default
nav_order: 13
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (13) | Cycubix Docs

### Compromising Availability <a href="#compromising_availability" id="compromising_availability"></a>

After successfully compromising confidentiality and integrity in the previous lessons, we now are going to compromise the third element of the CIA triad: **availability**.

The are many different ways to violate availability. If an account is deleted or the password gets changed, the actual owner cannot access it anymore. Attackers could also try to delete parts of the database making it useless or even dropping the whole database. Another way to compromise availability would be to per example revoke access-rights from admins or any other users, so that nobody gets access to (specific parts of) the database.

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

Now you are the top earner in your company. But do you see that? There seems to be a **access\_log** table, where all your actions have been logged to!

Better go and _delete it_ completely before anyone notices.

<figure><img src="../../../../../.gitbook/assets/sql injection 13.png" alt=""><figcaption></figcaption></figure>

#### Solution

* Given that actions log table cointains the history of all statements ran by all users we can use the command DROP with DDL. 
* Given the Hint "&#x54;_&#x68;e underlying SQL query looks like that: "SELECT \* FROM access\_log WHERE action LIKE '%" + action + "%_'", we can know the structure of the statement in the server. 
* The Like operator supports two main wildcard characters for pattern matching:

**Percent Sign (`%`)**: Represents zero, one, or multiple characters.

**Underscore (`_`)**: Represents a single character.

* `Answer: %'; DROP TABLE access_log;--`

<figure><img src="../../../../../.gitbook/assets/sql 13 2.png" alt=""><figcaption></figcaption></figure>
