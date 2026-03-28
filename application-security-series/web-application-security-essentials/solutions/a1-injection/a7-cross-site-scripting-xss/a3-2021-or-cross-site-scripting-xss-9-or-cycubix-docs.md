---
title: "A3:2021 | Cross Site Scripting (XSS) (9) | Cycubix Docs"
layout: default
nav_order: 9
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (9) | Cycubix Docs

### Reflected and DOM-Based XSS <a href="#reflected_and_dom_based_xss" id="reflected_and_dom_based_xss"></a>

DOM-based XSS is another form of reflected XSS. Both are triggered by sending a link with inputs reflected in the browser. The difference between DOM and 'traditional' reflected XSS is that, with DOM, the payload will never go to the server. The client will only ever process it.

* Attacker sends a malicious URL to the victim.
* Victim clicks on the link.
* That link may load a malicious web page or a web page they use (are logged into?) that has a vulnerable route/handler.
* If it’s a malicious web page, it may use its own JavaScript to attack another page/URL with a vulnerable route/handler.
* The vulnerable page renders the payload and executes an attack in the user’s context on that page/site.
* Attacker’s malicious script may run commands with the privileges of local account.

**Victim does not realize attack occurred** …​ Malicious attackers don’t use \<script>alert('xss')\</ script>
