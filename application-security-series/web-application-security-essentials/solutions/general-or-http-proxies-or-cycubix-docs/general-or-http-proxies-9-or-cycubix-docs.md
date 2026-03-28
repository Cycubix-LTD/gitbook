---
title: "General | HTTP Proxies (9) | Cycubix Docs"
layout: default
nav_order: 9
parent: "General | HTTP Proxies | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Proxies (9) | Cycubix Docs

## Burp Proxy

Another proxy you can use is Burp. One of the exercises in WebGoat can only be resolved with Burp and not with ZAP. 

You can only configure Burp manually. Please follow the steps described here first. 

You can download the Burp community edition as a [plain jar file](https://portswigger.net/burp/communitydownload)

```
java -jar burpsuite_community_v2.1.04.jar
```

The latest version of Burpsuit is [v2024.4.5](https://portswigger.net/burp/releases/professional-community-2024-4-5) (updated on May 31st 2024).

Choose `temporary project`, followed by `use burp defaults.`

Go to the proxy settings and change it to use port 8090.

<figure><img src="../../../../.gitbook/assets/burpsuite listeners.png" alt=""><figcaption></figcaption></figure>

On this page, you can also export the Burp certificate and import it into your browser. Similar to the instructions in previous pages.

Go to the proxy intercept page and click on the toggle so that intercept is switched off. 

<figure><img src="../../../../.gitbook/assets/burpsuite intercep off.png" alt=""><figcaption></figcaption></figure>



Then start a browser connected to the proxy and start using WebGoat. Now adjust the intercept request setting by extending the rule on what not to intercept:

Use e.g.: (^mvc$|^txt$|^woff$|^lesson$|^gif$|^jpg$|^png$|^css$|^js$|^ico$) Then enable the intercept by clicking on the earlier mentioned toggle.

An intercept will look like:

<figure><img src="../../../../.gitbook/assets/interception rules.png" alt=""><figcaption></figcaption></figure>

Finally, you can look at the history and add filters for the history and replay requests from this screen:

<figure><img src="../../../../.gitbook/assets/http history burpsuite.png" alt=""><figcaption></figcaption></figure>
