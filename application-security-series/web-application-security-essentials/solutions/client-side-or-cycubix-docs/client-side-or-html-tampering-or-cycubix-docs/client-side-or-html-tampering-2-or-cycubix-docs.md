---
title: "Client Side | HTML Tampering (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "Client Side | HTML Tampering | Cycubix Docs"
grand_parent: "Client Side | Cycubix Docs"
---
# Client Side | HTML Tampering (2) | Cycubix Docs

#### Try it yourself <a href="#try_it_yourself" id="try_it_yourself"></a>

In an online store you ordered a new TV, try to buy one or more TVs for a lower price.

<figure><img src="../../../../../.gitbook/assets/tampering 1.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Click on Checkout and intercept the request with ZAP.

<figure><img src="../../../../../.gitbook/assets/HTML TAMPERING.png" alt=""><figcaption></figcaption></figure>

* Sen the request to the Manual Request Editor and change the value of the tv for the following: 

```
QTY=1&Total=0
```

<figure><img src="../../../../../.gitbook/assets/tv discount.png" alt=""><figcaption></figcaption></figure>
