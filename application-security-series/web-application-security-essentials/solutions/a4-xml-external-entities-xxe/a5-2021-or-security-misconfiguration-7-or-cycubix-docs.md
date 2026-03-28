---
title: "A5:2021 | Security Misconfiguration (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (7) | Cycubix Docs

### Modern REST framework <a href="#modern_rest_framework" id="modern_rest_framework"></a>

In modern REST frameworks, the server might be able to accepts data formats that you as a developer did not think about. So this might result in JSON endpoints being vulnerable to XXE attacks.

Again same exercise but try to perform the same XML injection as we did in first assignment.

![](<../../../../.gitbook/assets/Screenshot 2020-04-28 at 16.15.55.png>)

#### Solution

* Hints: Take a look at the content type. Does the endpoint only accept json messages?. 
* Like in the previous exercise, we can use our Development Tools, Burp or Zap. 
* When you insert a comment see what is the answer. 

<figure><img src="../../../../.gitbook/assets/content type false.png" alt=""><figcaption></figcaption></figure>

* Let's change the content type from JSON to XXE. 

With Burp or ZAP

* Open the browser and turn the interceptor on Navigate into [http://localhost:8080/WebGoat](http://localhost:8080/WebGoat) and the corresponding lesson. 
* Submit a comment and intercept the request with the corresponding tool (ZAP or Burp). 
* Send the request to the Repeater (Burp) or Request Editor (ZAP). 
* Change the request accordingly: 

Edit header: from Content-Type: application/json to Content-Type: application/xml. 

Edit {"text":"your comment} to 

`<?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>`

<figure><img src="../../../../.gitbook/assets/xxe 7.png" alt=""><figcaption></figcaption></figure>



**With Development Tools**

* Open the _Development Tools_ in the browser, and go to the _Network_ tab.
* On WebGoat, post a comment.
* Find the request related to posting the comment. It will typically have a POST method.
* Change the body and header with: 

Edit the body with:

```
 <?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>. 
```

Edit the header 

```
Content-Type: application/json with Content-Type: application/xml
```



