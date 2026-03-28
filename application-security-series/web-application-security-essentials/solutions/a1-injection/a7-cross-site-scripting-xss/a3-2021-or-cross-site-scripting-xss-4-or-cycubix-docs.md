---
title: "A3:2021 | Cross Site Scripting (XSS) (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (4) | Cycubix Docs

### Why should we care? <a href="#why_should_we_care" id="why_should_we_care"></a>

#### XSS attacks may result in <a href="#xss_attacks_may_result_in" id="xss_attacks_may_result_in"></a>

* Stealing session cookies.
* Creating false requests.
* Creating false fields on a page to collect credentials.
* Redirecting your page to a "non-friendly" site.
* Creating requests that masquerade as a valid user.
* Stealing of confidential information.
* Execution of malicious code on an end-user system (active scripting).
*   Insertion of hostile and inappropriate content.

    ```
    <img src="http://malicious.site.com/image.jpg/>
    ">GoodYear recommends buying BridgeStone tires...
    ```

#### XSS attacks add validity to phishing attacks <a href="#xss_attacks_add_validity_to_phishing_attacks" id="xss_attacks_add_validity_to_phishing_attacks"></a>

* A valid domain is used in the URL.
