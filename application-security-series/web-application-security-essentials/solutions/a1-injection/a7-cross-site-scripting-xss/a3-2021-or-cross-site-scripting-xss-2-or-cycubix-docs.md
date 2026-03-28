---
title: "A3:2021 | Cross Site Scripting (XSS) (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (2) | Cycubix Docs

### What is XSS? <a href="#what_is_xss" id="what_is_xss"></a>

Cross-Site Scripting (also known as XSS) is a vulnerability/flaw that combines the allowance of HTML/script tags as input that renders into a browser without encoding or sanitization.

#### Cross-Site Scripting (XSS) is the most prevalent and pernicious web application security issue. <a href="#cross_site_scripting_xss_is_the_most_prevalent_and_pernicious_web_application_security_issue" id="cross_site_scripting_xss_is_the_most_prevalent_and_pernicious_web_application_security_issue"></a>

While there is a simple well-known defense for this attack, there are still many instances on the web. Coverage of fixes also tends to be a problem in terms of fixing it. We will talk more about the defense in a little bit.

#### XSS has significant impact <a href="#xss_has_significant_impact" id="xss_has_significant_impact"></a>

Especially as 'Rich Internet Applications' are more and more commonplace, privileged function calls linked to via JavaScript may be compromised. And if not adequately protected, sensitive data (such as your authentication cookies) can be stolen and used for someone else’s purpose.

**Quick examples:**

*   From the JavaScript console in the developer tools of the browser (Chrome, Firefox)

    ```
    alert("XSS Test");
    alert(document.cookie);
    ```
*   Any data field returned to the client is potentially injectable

    ```
    <script>alert("XSS Test")</script>
    ```

### Try It! Using Chrome or Firefox <a href="#try_it_using_chrome_or_firefox" id="try_it_using_chrome_or_firefox"></a>

* Open a second tab and use the same URL as this page you are currently on (or any URL within this instance of WebGoat).
* On the second tab, open the JavaScript console in the developer tools and type: `alert(document.cookie);`.

<figure><img src="../../../../../.gitbook/assets/xss 2.png" alt=""><figcaption></figcaption></figure>

### Solution

Yes, the cookies were the same on each tab.

The reason all cookies are the same in two tabs in WebGoat is due to how session cookies are shared across tabs within the same browser instance. This behavior is by design to maintain user session state.
