---
title: "A6:2021 | Vulnerable and Outdated Components (11) | Cycubix Docs"
layout: default
nav_order: 11
parent: "A6:2021 | Vulnerable and Outdated Components | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A6:2021 | Vulnerable and Outdated Components (11) | Cycubix Docs

### Some Examples of OSS Risk <a href="#some_examples_of_oss_risk" id="some_examples_of_oss_risk"></a>

#### Commons Collections <a href="#commons_collections" id="commons_collections"></a>

In November of 2015, the Apache Commons Collections component latest release was 8 years old. Commons Collections was considered a reliable and stable component. A researcher found a way to exploit a deserialization issue in Commons Collections resulting in a remote code execution. The next day…​ **everyone using Commons Collections was in a panic**.

Ref: [Thousands of Java applications vulnerable to nine-month-old remote code execution exploit](http://www.pcworld.com/article/3004633/business-security/thousands-of-java-applications-vulnerable-to-nine-month-old-remote-code-execution-exploit.html)

#### Dinis Cruz and Alvaro Munoz exploit of XStream <a href="#dinis_cruz_and_alvaro_munoz_exploit_of_xstream" id="dinis_cruz_and_alvaro_munoz_exploit_of_xstream"></a>

XStream, a relatively common XML and JSON parsing library, has a nasty little remote code execution.\
Ref: [Dinis Cruz Blog](https://diniscruz.blogspot.com/2013/12/xstream-remote-code-execution-exploit.html)\
[pwntester/XStreamPOC](https://github.com/pwntester/XStreamPOC)

You may want to read the article(s) before trying this lesson. Let’s see if you can figure out how to exploit this in WebGoat.
