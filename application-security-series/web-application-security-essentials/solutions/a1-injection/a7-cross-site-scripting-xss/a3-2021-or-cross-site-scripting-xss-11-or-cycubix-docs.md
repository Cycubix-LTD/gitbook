---
title: "A3:2021 | Cross Site Scripting (XSS) (11) | Cycubix Docs"
layout: default
nav_order: 11
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (11) | Cycubix Docs

### Try It! DOM-Based XSS <a href="#try_it_dom_based_xss" id="try_it_dom_based_xss"></a>

Some attacks are "blind". Fortunately, you have the server running here so you will be able to tell if you are successful. Use the route you just found and see if you can use the fact that it reflects a parameter from the route without encoding to execute an internal function in WebGoat. The function you want to execute is …​

**webgoat.customjs.phoneHome()**

Sure, you could just use console/debug to trigger it, but you need to trigger it via a URL in a new tab.

Once you do trigger it, a subsequent response will come to your browser’s console with a random number. Put that random number in below.

![](<../../../../../.gitbook/assets/Screenshot 2021-01-08 at 13.44.25.png>)

### Solution

* Hint: Open a new tab and navigate to the test-route you just figured out in the previous lesson. Your URL should look something like this:

_http://localhost:8080/WebGoat/start.mvc#REPLACE-WITH-THE-TEST-ROUTE/some\\\_parameters_

 _= http://localhost:8080/WebGoat/start.mvc#test/\<script>webgoat.customjs.phoneHome()<%2Fscript>._

* The script tags are used so that our JavaScript code gets executed when being rendered into the DOM.
* Once you navigate into the URL, your screen will show: 

<figure><img src="../../../../../.gitbook/assets/xss 1.png" alt=""><figcaption></figcaption></figure>

* Open your console, and see the phonehome invoked: 

<figure><img src="../../../../../.gitbook/assets/answer in console.png" alt=""><figcaption></figcaption></figure>

* Copy the number and paste it in the answer to lab: 

<figure><img src="../../../../../.gitbook/assets/xss 11.png" alt=""><figcaption></figcaption></figure>



