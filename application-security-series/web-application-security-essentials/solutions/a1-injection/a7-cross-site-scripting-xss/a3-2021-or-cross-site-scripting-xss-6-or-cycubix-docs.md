---
title: "A3:2021 | Cross Site Scripting (XSS) (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (6) | Cycubix Docs

### Reflected XSS scenario <a href="#reflected_xss_scenario" id="reflected_xss_scenario"></a>

* Attacker sends a malicious URL to the victim.
* Victim clicks on the link that loads a malicious web page.
* The malicious script embedded in the URL executes in the victim’s browser.
  * The script steals sensitive information, like the session id, and releases it to the attacker.

**Victim does not realize attack occurred**

<figure><img src="../../../../../.gitbook/assets/reflected xss.png" alt=""><figcaption></figcaption></figure>
