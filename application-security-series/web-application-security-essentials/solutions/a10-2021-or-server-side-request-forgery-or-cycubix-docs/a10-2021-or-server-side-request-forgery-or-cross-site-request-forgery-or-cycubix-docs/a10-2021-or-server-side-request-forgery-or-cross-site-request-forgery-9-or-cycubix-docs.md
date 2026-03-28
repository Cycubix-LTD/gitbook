---
title: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (9) | Cycubix Docs"
layout: default
nav_order: 9
parent: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (9) | Cycubix Docs

### CSRF Impact <a href="#csrf_impact" id="csrf_impact"></a>

The impact is limited only by what the logged in user can do (if the site/function/action is not protected properly). The areas that are really prone to CSRF attacks are IoT devices and 'smart' appliances. Sadly, many consumer-grade routers have also proven vulnerable to CSRF.

### CSRF solutions <a href="#csrf_solutions" id="csrf_solutions"></a>

#### Same site cookie attribute <a href="#same_site_cookie_attribute" id="same_site_cookie_attribute"></a>

This is a new extension which modern browsers support which limits the scope of the cookie such that it will only be attached to requests if those requests are 'same-site' For example requests for [`http://webgoat.org/something`](http://webgoat.org/something) will attach same-site cookies if the request is initiated from `webgoat.org`. 

There are two modes, strict and lax. The first one does not allow cross site request, this means when you are on github.com and you want to like it through Facebook (and Facebook specifies same-site as strict) you will be redirected to the login page, because the browser does not attach the cookie for Facebook. More information can be found here: [https://www.sjoerdlangkemper.nl/2016/04/14/preventing-csrf-with-samesite-cookie-attribute/](https://www.sjoerdlangkemper.nl/2016/04/14/preventing-csrf-with-samesite-cookie-attribute/)

#### Other protections <a href="#other_protections" id="other_protections"></a>

Fortunately, many (web) application frameworks now come with built in support to handle CSRF attacks. For example, Spring and Tomcat have this on by default. As long as you don’t turn it off (like it is in WebGoat), you should be safe from CSRF attacks.

See the following for more information on CSRF protections:

[https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site\_Request\_Forgery\_Prevention\_Cheat\_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html) (Prevention/Defense)

[https://owasp.org/www-community/attacks/csrf](https://owasp.org/www-community/attacks/csrf) (Attack)

[https://tomcat.apache.org/tomcat-7.0-doc/config/filter.html#CSRF\_Prevention\_Filter](https://tomcat.apache.org/tomcat-7.0-doc/config/filter.html#CSRF_Prevention_Filter) / [https://tomcat.apache.org/tomcat-8.0-doc/config/filter.html#CSRF\_Prevention\_Filter](https://tomcat.apache.org/tomcat-8.0-doc/config/filter.html#CSRF_Prevention_Filter) (Tomcat)

[https://docs.spring.io/spring-security/site/docs/current/reference/html5/#csrf](https://docs.spring.io/spring-security/site/docs/current/reference/html5/#csrf)
