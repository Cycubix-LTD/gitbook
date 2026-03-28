---
title: "A6:2021 | Vulnerable and Outdated Components (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A6:2021 | Vulnerable and Outdated Components | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A6:2021 | Vulnerable and Outdated Components (5) | Cycubix Docs

### The exploit is not always in "your" code <a href="#the_exploit_is_not_always_in_your_code" id="the_exploit_is_not_always_in_your_code"></a>

Below is an example of using the same WebGoat source code, but different versions of the jquery-ui component. One is exploitable; one is not.

#### jquery-ui:1.10.4 <a href="#jquery_ui1_10_4" id="jquery_ui1_10_4"></a>

This example allows the user to specify the content of the "closeText" for the jquery-ui dialog. This is an unlikely development scenario, however the jquery-ui dialog (TBD - show exploit link) does not defend against XSS in the button text of the close dialog.



<figure><img src="../../../../.gitbook/assets/the exploit is not always your code.png" alt=""><figcaption></figcaption></figure>

#### jquery-ui:1.12.0 Not Vulnerable <a href="#jquery_ui1_12_0_not_vulnerable" id="jquery_ui1_12_0_not_vulnerable"></a>

Using the same WebGoat source code but upgrading the jquery-ui library to a non-vulnerable version eliminates the exploit.

<figure><img src="../../../../.gitbook/assets/the exploit is not always your code 2.png" alt=""><figcaption></figcaption></figure>

After clicking on both codes, analyze the following answer:

<figure><img src="../../../../.gitbook/assets/A6 1.png" alt=""><figcaption></figcaption></figure>
