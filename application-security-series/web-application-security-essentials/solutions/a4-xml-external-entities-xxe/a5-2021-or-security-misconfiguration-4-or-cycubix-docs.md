---
title: "A5:2021 | Security Misconfiguration (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (4) | Cycubix Docs

### Let’s try <a href="#lets_try" id="lets_try"></a>

In this assignment, you will add a comment to the photo, when submitting the form try to execute an XXE injection with the comments field. Try listing the root directory of the filesystem.

![](<../../../../.gitbook/assets/Screenshot 2020-04-28 at 16.15.55.png>)

#### Solution

* Hints: Try submitting the form and see what happens. Use ZAP/Burp to intercept the request and try to include your own DTD. Try to include a doctype "(\<!DOCTYPE...)" in the xml. This exercise is all about understanding how the XXE injection works. 

```
The include can be as follows: <!DOCTYPE user [<!ENTITY root SYSTEM "file:///"> ]>e
```

* Do not forget to reference the entity. 

```
In the comment you should references: <comment><text>&root;test</text></comment>
```

* For this exercise we can use Burp, Zap or Developer Tools. First open the Intercepter (Burp) or Break (Zap). Then submit a comment on WebGoat. Analyze the request. 

<figure><img src="../../../../.gitbook/assets/xxe i am a cat.png" alt=""><figcaption></figcaption></figure>

* Analyze the format of the text "I am a cat" and the path of the Post request. 
* In the case of BurpSuite or ZAP, replace the text in the button for the following, to probe that the server is vulnerable: 

`<?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>`

* With Developer tools you can do the following steps: 

Open the _Development Tools_ in the browser, and go to the _Network_ tab.

On WebGoat, post a comment.

Locate the query to `simple` in the _Network_ tab and click on _Edit and Resend_.

Edit the body with: 

`<?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>`

<figure><img src="../../../../.gitbook/assets/lesson completed xxe 4.png" alt=""><figcaption></figcaption></figure>

* Details about the solution come in the following page. 

