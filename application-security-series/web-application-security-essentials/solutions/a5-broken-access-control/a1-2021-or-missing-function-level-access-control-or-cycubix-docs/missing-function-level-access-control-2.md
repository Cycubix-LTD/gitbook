---
title: "A1:2021 | Missing Function Level Access Control (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A1:2021 | Missing Function Level Access Control | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Missing Function Level Access Control (2) | Cycubix Docs

Relying on Obscurity

If you are relying on HTML, CSS or javascript to hide links that users don’t normally access. It’s a little older, but there was a case of a network router trying to protect (hide) admin functions with javascript in the UI [https://www.wired.com/2009/10/routers-still-vulnerable](https://www.wired.com/2009/10/routers-still-vulnerable)

#### Finding Hidden Items <a href="#finding_hidden_items" id="finding_hidden_items"></a>

There are usually hints to finding functionality the UI (User Interface) does not openly expose in:

* HTML or javascript comments.
* Commented out elements.
* Items hidden via css controls/classes.

#### Your Mission <a href="#your_mission" id="your_mission"></a>

Find two menu items not visible in menu below that are or would be of interest to an attacker/malicious user and put the labels for those menu items (there are no links right now in the menus).

The following capture will show you what the user can see: 

<figure><img src="../../../../../.gitbook/assets/missing function level access 3.png" alt=""><figcaption></figcaption></figure>

* Open the developer tools and go to Inspect Element. 
* Look for indications of something that would not be available to a typical user. Such as:

<figure><img src="../../../../../.gitbook/assets/hidden items conifg.png" alt=""><figcaption></figcaption></figure>

* Type "Users" and "Config" in the responses. 

<figure><img src="../../../../../.gitbook/assets/results lab missing function control access.png" alt=""><figcaption></figcaption></figure>

Don't forget the urls for the upcoming lab! 
