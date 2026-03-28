---
title: "A3:2021 | Cross Site Scripting Stored (2)"
layout: default
nav_order: 2
parent: "A3:2021 | Cross Site Scripting Stored | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting Stored (2)

### Stored XSS <a href="#stored_xss" id="stored_xss"></a>

Stored Cross-Site Scripting is different in that the payload is persisted (stored) instead of passed/injected via a link.

### Stored XSS Scenario <a href="#stored_xss_scenario" id="stored_xss_scenario"></a>

* Attacker posts malicious script to a message board.
* Message is stored in a server database.
* Victim reads the message.
* The malicious script embedded in the message board post executes in the victim’s browser.
  * The script steals sensitive information, like the session id, and releases it to the attacker.

**Victim does not realize attack occurred**
