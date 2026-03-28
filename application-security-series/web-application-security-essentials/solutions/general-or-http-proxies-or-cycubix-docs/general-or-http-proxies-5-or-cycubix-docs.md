---
title: "General | HTTP Proxies (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "General | HTTP Proxies | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Proxies (5) | Cycubix Docs

## Configure a breakpoint filter

Before we start diving into intercepting requests with ZAP, we need to exclude the internal requests from the WebGoat framework. Otherwise, ZAP will also stop at all the requests which are only necessary for the inner working of WebGoat. 

Basically, a breakpoint is configured that will intercept requests when the request header contains a POST. You can add other rules as long as the polling `.mvc` messages will be excluded. As this would be annoying.

Set the breakpoint as follows:

1. Set Up the breakpoint. 

<figure><img src="../../../../.gitbook/assets/http proxies 5 .png" alt=""><figcaption></figcaption></figure>

2. Check your active breakpoints. If you click on the checkbox, you can temporarily deactivate them and enable them again before intercepting the request. \*\*Do not use the green/red button.

<figure><img src="../../../../.gitbook/assets/http proxies 5 2.png" alt=""><figcaption></figcaption></figure>

3. Once you are intercepting requests and a request is made, it should look something like this:

<figure><img src="../../../../.gitbook/assets/http proxies 5 3.png" alt=""><figcaption></figcaption></figure>

4. Set up the intercept as noted above and then submit the form/request below by clicking the submit button. 

<figure><img src="../../../../.gitbook/assets/HTTP proxies 5 4.png" alt=""><figcaption></figcaption></figure>

5. Once you submit the request, your request should look like this: 

<figure><img src="../../../../.gitbook/assets/HTTP proxies 5 5.png" alt=""><figcaption></figcaption></figure>

6. As your request is intercepted, make the following changes:

* Change the Method to GET

<figure><img src="../../../../.gitbook/assets/HTTP proxies 5 6.png" alt=""><figcaption></figcaption></figure>

* Add a header 'x-request-intercepted:true'

<figure><img src="../../../../.gitbook/assets/http proxies 5 7.png" alt=""><figcaption></figcaption></figure>

* Remove the request body and instead send 'changeMe' as a query string parameter and set the value to 'Requests are tampered easily' (without the single quotes)

<figure><img src="../../../../.gitbook/assets/http proxies 5 8.png" alt=""><figcaption></figcaption></figure>

