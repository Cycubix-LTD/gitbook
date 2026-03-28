---
title: "A3:2021 | Cross Site Scripting (XSS) (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (7) | Cycubix Docs

### Try It! Reflected XSS <a href="#try_it_reflected_xss" id="try_it_reflected_xss"></a>

Identify which field is susceptible to XSS

It is always a good practice to validate all input on the server-side. XSS can occur when unvalidated user input is used in an HTTP response. In a reflected XSS attack, an attacker can craft a URL with the attack script and post it to another website, email it, or otherwise get a victim to click on it.

An easy way to find out if a field is vulnerable to an XSS attack is to use the _alert()_ or _console.log()_ methods. Use one of them to find out which field is vulnerable.

<figure><img src="../../../../../.gitbook/assets/reflected xss 1.png" alt=""><figcaption></figcaption></figure>

### Solution

* The hint provided says "Think about how the inputs are presumably processed by the application.". 
* We can start by positioning in the field of credit card number. Select inspect to open developer tools. 
* Paste after the credit card number the following script: 

`<script>alert(2)</script>`

* What information send to the application gets reflected back after being submitted?

<figure><img src="../../../../../.gitbook/assets/local host says 2.png" alt=""><figcaption></figcaption></figure>

* Your purchase will be completed as follow: 



<figure><img src="../../../../../.gitbook/assets/script alerts.png" alt=""><figcaption></figcaption></figure>



