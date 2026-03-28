---
title: "A7:2021 | Password Reset (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A7:2021 | Password Reset | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7:2021 | Password Reset (2) | Cycubix Docs

### Email functionality with WebWolf <a href="#email_functionality_with_webwolf" id="email_functionality_with_webwolf"></a>

Let’s first do a simple assignment to make sure you are able to read e-mails with WebWolf, first start WebWolf (see [here](http://127.0.0.1:9090/WebWolf/home)) In the reset page below send an e-mail to `username@webgoat.org` (part behind the @ is not important) Open WebWolf and read the e-mail and login with your username and the password provided in the e-mail.

<figure><img src="../../../../../.gitbook/assets/email functionality.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Log in to WebWolf. If you cannot open it from WebGoat open a new tab and type: [http://localhost:9090/WebWolf](http://localhost:9090/WebWolf). 
* Log in with your username and select "forgot your password". Type your user and go into WebWolf to check the email. 
* You will see a message with the reseted password, go back to WebGoat and type the password from your user. 
