---
description: Learn what type of HTTP command WebGoat used for this lesson. Discover the solution to the HTTP quiz we offered as part of our web application security course.
title: "General | HTTP Basics (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "General | HTTP Basics | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Basics (3) | Cycubix Docs

## The Quiz <a href="#the_quiz" id="the_quiz"></a>

What type of HTTP command did WebGoat use for this lesson. A POST or a GET.

<figure><img src="../../../../.gitbook/assets/http basics 2.png" alt=""><figcaption></figcaption></figure>

## Hints

> ℹ️ **Info**
>
> Turn on Show Parameters or other features.

> ℹ️ **Info**
>
> Try to intercept the request with ZAP

## Solution

The HTTP request observed in the previous exercise was a POST message. The magic number is hidden in the web page's JavaScript. One of the methods to view this is to right click on the web page and select "Inspect".

In the "Body" section, search for the phrase "magic" until you identify the value stored by the hidden `magic_num` field.

## Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).

