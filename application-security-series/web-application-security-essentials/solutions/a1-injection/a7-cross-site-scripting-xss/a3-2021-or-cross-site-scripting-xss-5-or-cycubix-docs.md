---
title: "A3:2021 | Cross Site Scripting (XSS) (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (5) | Cycubix Docs

### Types of XSS <a href="#types_of_xss" id="types_of_xss"></a>

#### Reflected <a href="#reflected" id="reflected"></a>

* Malicious content from a user request is displayed to the user in a web browser.
* Malicious content is written into the page after from server response.
* Social engineering is required.
* Runs with browser privileges inherited from the user in a browser.

#### DOM-based (also technically reflected) <a href="#dom_based_also_technically_reflected" id="dom_based_also_technically_reflected"></a>

* Client-side scripts use malicious content from a user request to write HTML to its page.
* Similar to reflected XSS.
* Runs with browser privileges inherited from the user in a browser.

#### Stored or persistent <a href="#stored_or_persistent" id="stored_or_persistent"></a>

* Malicious content is stored on the server ( in a database, file system, or other objects) and later displayed to users in a web browser.
* Social engineering is not required.
