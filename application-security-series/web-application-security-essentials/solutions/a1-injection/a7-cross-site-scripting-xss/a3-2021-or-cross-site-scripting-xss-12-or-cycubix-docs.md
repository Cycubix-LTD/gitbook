---
title: "A3:2021 | Cross Site Scripting (XSS) (12) | Cycubix Docs"
layout: default
nav_order: 12
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (12) | Cycubix Docs

Now it is time for a quiz! It is recommended to check the OWASP Cross-Site Scripting explanations [https://www.owasp.org/index.php/Cross-site\_Scripting\_(XSS](https://owasp.org/www-community/attacks/xss/)) . Answer all questions correctly to complete the assignment.

### Solution

**1. Are trusted websites immune to XSS attacks?**

Solution 4: No because the browser trusts the website if it is acknowledged trusted, then the browser does not know that the script is malicious.

**2. When do XSS attacks occur?**

Solution 3: The data is included in dynamic content that is sent to a web user without being validated for malicious content.

**3. What are Stored XSS attacks?**

Solution 1: The script is permanently stored on the server and the victim gets the malicious script when requesting information from the server.

**4. What are Reflected XSS attacks?**

Solution 2: They reflect the injected script off the web server. That occurs when input sent to the web server is part of the request.

**5. Is JavaScript the only way to perform XSS attacks?**

Solution 4: No there are many other ways. Like HTML, Flash or any other type of code that the browser executes.
