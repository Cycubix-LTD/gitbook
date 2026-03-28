---
title: "A5:2021 | Security Misconfiguration (13) | Cycubix Docs"
layout: default
nav_order: 13
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (13) | Cycubix Docs

#### Find XXE issues with static code analysis <a href="#find_xxe_issues_with_static_code_analysis" id="find_xxe_issues_with_static_code_analysis"></a>

Static code analysis can help identify vulnerabilities in code. A well known tool for static code analysis is SonarQube. When you run a code scan on the source code of WebGoat, you will get something like:

<figure><img src="../../../../.gitbook/assets/xxe 13 1.png" alt=""><figcaption></figcaption></figure>

If you select the XXE category it will show you the location of the XXE vulnerability.

<figure><img src="../../../../.gitbook/assets/xxe 13 2.png" alt=""><figcaption></figcaption></figure>

The next step is to identify whether this is a true issue or a false positive. As you already know from the challenge exercise, this is a real issue. In this case it is put in intentionally.

SonarQube also shows you what you could do to fix this.

<figure><img src="../../../../.gitbook/assets/xxe 13 3.png" alt=""><figcaption></figcaption></figure>

If you click on the red button above, you can try to do the XXE challenges again and you will notice that the vulnerabilities are mitigated.

<br>
