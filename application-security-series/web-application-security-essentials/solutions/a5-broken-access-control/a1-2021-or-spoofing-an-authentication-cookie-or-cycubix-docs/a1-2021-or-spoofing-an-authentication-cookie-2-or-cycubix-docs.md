---
title: "A1:2021 | Spoofing an Authentication Cookie (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A1:2021 | Spoofing an Authentication Cookie | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Spoofing an Authentication Cookie (2) | Cycubix Docs

Attempt to bypass the authentication mechanism by spoofing an authentication cookie.

**Notes about the login system**

* When a valid authentication cookie is received, the system will automatically log in the user.
* If a cookie is not sent, but the provided credentials are correct, the system will generate an authentication cookie.
* Login attempts will be denied under any other circumstances.

\*Please pay close attention to the feedback messages you receive during the attacks.\*

Known credentials:

| user name | password |
| --------- | -------- |
| webgoat   | webgoat  |
| admin     | admin    |

**Goal**

Once you have a clear understanding of how the authentication cookie is generated, attempt to _spoof_ the cookie and log in as Tom.

<figure><img src="../../../../../.gitbook/assets/SPOOFING COOKIE.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Turn on the Interceptor (Burp) or Break (ZAP).
* Enter the known user credentials (webgoat/admin). 
* What results you can compare: WebGoat and Admin have their own spoofed cookie but as you continue to log in you will notice that the spoof cookie for each login maintains its value. 

Admin Cookie= NDE1MTc5NjI3MjU3NTg1NTRjNTc2ZTY5NmQ2NDYx

WebGoat Cookie= NDE1MTc5NjI3MjU3NTg1NTRjNTc3NDYxNmY2NzYyNjU3Nw==

What is the encoding Scheme?: [https://www.base64decode.org/](https://www.base64decode.org/)

* After you encode the spoofed cookies into UTF-8 you will receive the folowing values: 

Admin= 41517962725758554c576e696d6461

WebGoat= 41517962725758554c5774616f67626577

* UTF-8 encodes in HEX values, meaning in 8 BITS. We can use a Converter from HEX to Text ([https://codebeautify.org/hex-string-converter](https://codebeautify.org/hex-string-converter)). 

Admin spoofed cookie into text= AQybrWXULW**nimda**

WebGoat spoofed cookie into text= AQybrWXULW**taogbew**

We can see the characteristics of the encoding values, keeping the first part the same and spelling backwards the user name. 

* Now go to the section of string reverser on CodeBeautify to reverse the string: 

Admin= adminWLUXWrbyQA

WebGoat= webgoatWLUXWrbyQA

* Now replace on the reversed string Admin or WebGoat into TOM. 

AQybrWXULWmoT

* Then go back to the section of String to HEX in CodeBeautify, and encode the above string. 

41517962725758554c576d6f54

* Go into the Base64Encode Website and Encode the string into UTF-8. 

NDE1MTc5NjI3MjU3NTg1NTRjNTc2ZDZmNTQ=

* How do we authenticate the new authentication cookie? 

Find the corresponding POST request. Forward it to the Repeater (Burp) or Manual Reuqest Editor (ZAP). 

Add after Cookie JSESSIONID the spoofed authentication. 

<figure><img src="../../../../../.gitbook/assets/cookie spoof ok 1.png" alt=""><figcaption></figcaption></figure>

Send the Request and you will get the following message: 

<figure><img src="../../../../../.gitbook/assets/cookie spoof ok 2.png" alt=""><figcaption></figcaption></figure>

With the manipulation of the authenticated cookie we can now impersonate another user, in this case TOM.  
