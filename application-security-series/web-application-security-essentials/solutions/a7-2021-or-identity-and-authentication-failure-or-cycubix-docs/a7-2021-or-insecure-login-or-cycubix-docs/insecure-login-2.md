---
title: "A7:2021 | Insecure Login (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A7:2021 | Insecure Login | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7:2021 | Insecure Login (2) | Cycubix Docs

#### Let’s try <a href="#lets_try" id="lets_try"></a>

Click the "log in" button to send a request containing login credentials of another user. Then, write these credentials into the appropriate fields and submit to confirm. Try using a packet sniffer to intercept the request.

![](<../../../../../.gitbook/assets/Screenshot 2020-04-28 at 15.59.32.png>)

#### Solution

* Open the _Development Tools_ in the browser, and go to the _Network_ tab.
* On WebGoat, click on **Log in**.
* Locate the query to `start.mc` in the _Network_ tab and click on _Parameters_.
* Notice the parameters `{"username":"CaptainJack","password":"BlackPearl"}`.

<figure><img src="../../../../../.gitbook/assets/insecure login.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/insecure ligin2.png" alt=""><figcaption></figcaption></figure>
