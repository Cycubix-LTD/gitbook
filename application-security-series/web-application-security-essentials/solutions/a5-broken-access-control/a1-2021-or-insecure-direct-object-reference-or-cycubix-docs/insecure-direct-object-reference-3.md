---
title: "A1:2021 | Insecure Direct Object Reference (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A1:2021 | Insecure Direct Object Reference | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Insecure Direct Object Reference (3) | Cycubix Docs

Observing Differences & Behaviors

A consistent principle from the offensive side of AppSec is to view differences from the raw response to what is visible. In other words (as you may have already noted in the client-side filtering lesson), there is often data in the raw response that doesn’t show up on the screen/page. 

#### Solution

**Developer Tools**

* Open the developer tools to see the HTTP request. 

<figure><img src="../../../../../.gitbook/assets/IDOR view profile (1).png" alt=""><figcaption></figcaption></figure>

* What data that shows up on the screen is also in the network information?. 
* Look for profile tab and see which fields are not visible in the profile. Submit your answer. 

<figure><img src="../../../../../.gitbook/assets/IDOR attributes inspect.png" alt=""><figcaption></figcaption></figure>

**ZAP**

* Select view profile on the corresponding page of WebGoat.
* Intercept the request with ZAP, and open the request in the Manual Request Editor. Send the request and check the response. You will be able to see the hidden items. 

<figure><img src="../../../../../.gitbook/assets/hidden items ok.png" alt=""><figcaption></figcaption></figure>

* Type your request "role" and "userid" in WebGoat. 
