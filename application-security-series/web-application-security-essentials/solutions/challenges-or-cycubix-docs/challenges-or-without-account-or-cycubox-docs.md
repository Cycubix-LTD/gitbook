---
title: "Challenges | Without Account | Cycubox Docs"
layout: default
nav_order: 4
parent: "Challenges | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# Challenges | Without Account | Cycubox Docs

Can you still vote?

<figure><img src="../../../../.gitbook/assets/voting.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Try to change the average rating and intercept the request with ZAP or BURP. 

<figure><img src="../../../../.gitbook/assets/without account 1.png" alt=""><figcaption></figcaption></figure>

* As we intercept the request we can try with different request method and examine the response. 

<figure><img src="../../../../.gitbook/assets/POST method not supported.png" alt=""><figcaption></figcaption></figure>

We can see that the POST method is not a supported exception. We can try with other methods to see if there is an exception that is supported. 

* The HEAD method returns the Flag. 

<figure><img src="../../../../.gitbook/assets/submit flag.png" alt=""><figcaption></figcaption></figure>

