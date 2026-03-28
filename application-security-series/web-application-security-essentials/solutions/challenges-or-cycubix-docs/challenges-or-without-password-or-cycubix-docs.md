---
title: "Challenges | Without password | Cycubix Docs"
layout: default
nav_order: 2
parent: "Challenges | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# Challenges | Without password | Cycubix Docs

Can you login as Larry?

[LOGIN](http://localhost:8080/WebGoat/start.mvc?username=luzclarita7)

<figure><img src="../../../../.gitbook/assets/log in as larry.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Intercept the request with ZAP or Burp. 

<figure><img src="../../../../.gitbook/assets/new log in.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/larry.png" alt=""><figcaption></figcaption></figure>

* If we modified the password we will get a responde saying there is a Java SQL Exception. 

<figure><img src="../../../../.gitbook/assets/log in with colon.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/content modified.png" alt=""><figcaption></figcaption></figure>

* We will see from the Java SQL exception that we have a SQL Injection. We will try to change the password accordingly. 
* We can use the 'OR' statement to manipulate and have a true return, therefore bypassing authentication checks. 

<figure><img src="../../../../.gitbook/assets/OR Statement.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/get your flag.png" alt=""><figcaption></figcaption></figure>
