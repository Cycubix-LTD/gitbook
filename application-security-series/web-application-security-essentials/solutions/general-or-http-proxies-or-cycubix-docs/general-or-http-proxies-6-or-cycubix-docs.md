---
title: "General | HTTP Proxies (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "General | HTTP Proxies | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Proxies (6) | Cycubix Docs

## Edit & Resend functionality on ZAP

Instead of intercepting the request, there is also an option to resend the same request again within ZAP. It helps you solve an assignment because you do not have to switch to ZAP, enable the intercept button, go back to WebGoat and perform the request again from within the browser.

Let’s look at an example. We are going to use the e-mail example from the WebWolf introduction lesson. 

1. Generate a request for `/WebGoat/WebWolf/mail`, in the "History" window, select the URL you want to resend right click on the URL and select `Open/Resend with Request Editor`.  You can also find the request in the left pane of ZAP as indicated with the red arrow in the image below: 

<figure><img src="../../../../.gitbook/assets/http proxies 6 bis 4 (1).png" alt=""><figcaption></figcaption></figure>

2. Open the manual request editor by clicking with the right cursor and select "Open/Resend with Request Editor". 
3. A new window will open, and here, you can modify the request, for example, change the e-mail address to someone else and send it again. In the response tab, you can inspect the response of the request. 

<figure><img src="../../../../.gitbook/assets/http proxies 6 bis 7.png" alt=""><figcaption></figcaption></figure>

You can modify the request parameters as needed and resend it to see how WebGoat responds.

<figure><img src="../../../../.gitbook/assets/http proxies 6 bis 6 (1).png" alt=""><figcaption></figcaption></figure>

The response will show a solved message in some assignments, but sometimes you get a code/flag that you need to submit in WebGoat to complete the assignment. Always be on the lookout for a response. 

If you solved the assignment by making a request, WebGoat would automatically mark the lesson as solved.



