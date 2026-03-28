---
title: "A10:2021 | Server Side Request Forgery (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A10:2021 | Client Side Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery (4) | Cycubix Docs

### Prevent <a href="#prevent" id="prevent"></a>

To prevent SSRF vulnerabilities in web applications, it is recommended to adhere to the following guidelines:

* Use a whitelist of allowed domains, resources, and protocols from where the webserver can fetch resources.
* Any input accepted from the user should be validated and rejected if it does not match the positive specification expected.
* If possible, do not accept user input in functions that control where the webserver can fetch resources.

### References <a href="#references" id="references"></a>

[https://cheatsheetseries.owasp.org/cheatsheets/Server\_Side\_Request\_Forgery\_Prevention\_Cheat\_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
