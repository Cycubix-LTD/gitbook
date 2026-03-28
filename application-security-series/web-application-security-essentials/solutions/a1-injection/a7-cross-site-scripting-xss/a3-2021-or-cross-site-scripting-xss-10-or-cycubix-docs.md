---
title: "A3:2021 | Cross Site Scripting (XSS) (10) | Cycubix Docs"
layout: default
nav_order: 10
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (10) | Cycubix Docs

### Identify potential for DOM-Based XSS <a href="#identify_potential_for_dom_based_xss" id="identify_potential_for_dom_based_xss"></a>

DOM-Based XSS can usually be found by looking for the route configurations in the client-side code. Look for a route that takes inputs that are "reflected" to the page.

For this example, you will want to look for some 'test' code in the route handlers (WebGoat uses backbone as its primary JavaScript library). Sometimes, test code gets left in production (and often test code is simple and lacks security or quality controls!).

Your objective is to find the route and exploit it. First though, what is the base route? As an example, look at the URL for this lesson …​it should look something like /WebGoat/start.mvc#lesson/CrossSiteScripting.lesson/9. The 'base route' in this case is: **start.mvc#lesson/** The **CrossSiteScripting.lesson/9** after that are parameters that are processed by the JavaScript route handler.

So, what is the route for the test code that stayed in the app during production? To answer this question, you have to check the JavaScript source.

<figure><img src="../../../../../.gitbook/assets/xss 10.png" alt=""><figcaption></figcaption></figure>



**Solution**

* Hint: o search through the client side code, use the developer tools of your browser. (If you don't know how to use them, check the Developer Tools Lesson in the general category.)
* Since you are looking for application code, check the WebGoat/js/goatApp folder for a file that could handle the routes.

<figure><img src="../../../../../.gitbook/assets/xss 10 goatapp.png" alt=""><figcaption></figcaption></figure>

* Then. go into view to find the file GoatRouter.js. Look for **routes** to find `'test/:param': 'testRoute'`.

<figure><img src="../../../../../.gitbook/assets/GOAT Router.png" alt=""><figcaption></figcaption></figure>

* As it says in the lesson  The 'base route' in this case is: **start.mvc#lesson/** . 
* If we change lesson for test, then expected answer is then `start.mvc#test/`.

**Troubleshooting**

* If before arriving to the expected answer you type routes like test/:param, start.mvc#test/:param, etc. Reset the lesson and type again: `start.mvc#test/`.

