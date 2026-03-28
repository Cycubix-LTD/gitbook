---
title: "Client Side | HTML Tampering (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "Client Side | HTML Tampering | Cycubix Docs"
grand_parent: "Client Side | Cycubix Docs"
---
# Client Side | HTML Tampering (3) | Cycubix Docs

#### Mitigation <a href="#mitigation" id="mitigation"></a>

In this simple example you noticed that the price is calculated client-side and sent to the server. The server accepted the input as a given and did not calculate the price again. One of the mitigations in this case is to look up the price of the television in your database and calculate the total price again.

In a real application you should never rely on client side validation. It is important to verify all the input sent by the client. Always remember: **NEVER TRUST INPUT SENT BY A CLIENT.**

**References**

[https://cheatsheetseries.owasp.org/cheatsheets/Input\_Validation\_Cheat\_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)

