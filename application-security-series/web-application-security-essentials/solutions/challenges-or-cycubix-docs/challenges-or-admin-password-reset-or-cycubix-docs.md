---
title: "Challenges | Admin Password Reset | Cycubix Docs"
layout: default
nav_order: 3
parent: "Challenges | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# Challenges | Admin Password Reset | Cycubix Docs

Try to reset the password for admin.

<figure><img src="../../../../.gitbook/assets/reset passwrod for admin.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Send yourself and email thorugh WebWolf ([http://localhost:9090/WebWolf](http://localhost:9090/WebWolf)). <br>

<figure><img src="../../../../.gitbook/assets/passwordreset.png" alt=""><figcaption></figcaption></figure>

* The link you receive should have the following format: [http://localhost:8080/WebGoat/challenge/7/reset-password/867ef18bf000c0195c83161caf758c19](http://localhost:8080/WebGoat/challenge/7/reset-password/867ef18bf000c0195c83161caf758c19)
* What we need to find is the Hash Value. We can examine the source code.  It is better to download the zip source code: [https://github.com/WebGoat/WebGoat/releases](https://github.com/WebGoat/WebGoat/releases)
* You will see that there is a static admin password link: 

<figure><img src="../../../../.gitbook/assets/admin has a fix reset link.png" alt=""><figcaption></figcaption></figure>

* Now, go into the solutions constante page: [https://github.com/WebGoat/WebGoat/blob/eed0feed061293e3c3f9d21ff672b68b55fc5e5d/webgoat-lessons/challenge/src/main/java/org/owasp/webgoat/challenges/SolutionConstants.java](https://github.com/WebGoat/WebGoat/blob/eed0feed061293e3c3f9d21ff672b68b55fc5e5d/webgoat-lessons/challenge/src/main/java/org/owasp/webgoat/challenges/SolutionConstants.java)

<figure><img src="../../../../.gitbook/assets/admin reset link.png" alt=""><figcaption></figcaption></figure>

* Compose the link according to the above information: 

[http://localhost:8080/WebGoat/challenge/7/reset-password/867ef18bf000c0195c83161caf758c19](http://localhost:8080/WebGoat/challenge/7/reset-password/867ef18bf000c0195c83161caf758c19)

Replace with the hash value: 

<figure><img src="../../../../.gitbook/assets/kitty flag.png" alt=""><figcaption></figcaption></figure>

