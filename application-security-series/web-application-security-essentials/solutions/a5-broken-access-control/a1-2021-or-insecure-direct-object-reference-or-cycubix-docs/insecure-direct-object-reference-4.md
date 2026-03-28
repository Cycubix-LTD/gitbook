---
title: "A1:2021 | Insecure Direct Object Reference (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A1:2021 | Insecure Direct Object Reference | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Insecure Direct Object Reference (4) | Cycubix Docs

## Guessing & Predicting Patterns <a href="#guessing_predicting_patterns" id="guessing_predicting_patterns"></a>

### **View Your Own Profile Another Way**

To view your own profile explicitly using a direct object reference in a RESTful application, a common pattern is to use `/profile/me`. This route is typically mapped to the authenticated user's profile data, making it easily distinguishable from `/profile/{userId}` paths that are used to view other users' profiles.

So, what do you think is a likely pattern to view your own profile explicitly using a direct object reference?

![](<../../../../../.gitbook/assets/Screenshot 2020-04-28 at 16.33.14.png>)

### **Hints**

> ℹ️ **Info**
>
> Look at the previous request for profile, this is similar

> ℹ️ **Info**
>
> You will need data from the previous request for your own profile

> ℹ️ **Info**
>
> Append your id to the previous request (i.e. .../profile/{yourId})

### **Solution**

#### **Developer Tools**

* To find the solution we need to understand how URL parameters or paths can be manipulated to access information you should not access under normal circumstances. This is done by exploiting an Insecure Direct Object Reference (IDOR) vulnerability.

<figure><img src="../../../../../.gitbook/assets/IDOR profile user id (1).png" alt=""><figcaption></figcaption></figure>

* Let's start by opening the Developer Tools. Go to the "Network" tab to monitor network requests when you perform actions on the page.
* Look for requests that include object IDs in the URL or request parameters. 

#### Zap

* Let's check Zap, see the path in the request. 

<figure><img src="../../../../../.gitbook/assets/IDOR path.png" alt=""><figcaption></figcaption></figure>

*  You can know that viewing Profile is to request the URL of "WebGoat/IDOR/profile".
* We know from the previous exercise that the userid is 2342384. 
* So, the correct answer is "WebGoat/IDOR/profile/2342384".

<figure><img src="../../../../../.gitbook/assets/IDOR alternate url for profile (1).png" alt=""><figcaption></figcaption></figure>
