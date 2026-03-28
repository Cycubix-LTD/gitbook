---
title: "General | HTTP Proxies (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "General | HTTP Proxies | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Proxies (3) | Cycubix Docs

## Setting Up a Browser

If you use the latest ZAP version (>= 2.15.0), you only need to start ZAP and click the browser button to be able to proxy, see image below:

<figure><img src="../../../../.gitbook/assets/http proxies part 3.png" alt=""><figcaption></figcaption></figure>

In the browser type: [https://localhost:8080/WebGoat](https://localhost:8080/WebGoat), you should see WebGoat and the ZAP Heads On Display (if you use  ZAP as the proxy) (\*). 

You might notice that this is the Dutch login screen. The browser determines the language settings. For some pages, there will be some local translations. You can contribute to WebGoat and add more for your preferred language. You can disable the Heads On Display by clicking on the highlighted button. You can learn about the OWASP ZAP HUD on their website. For now, we recommend disabling it as it kind of blocks the menu items.

You should see the following in OWASP ZAP on the history panel:

<figure><img src="../../../../.gitbook/assets/http proxies part 3 bis.png" alt=""><figcaption></figcaption></figure>

On the next page, we will show how to filter these requests to see only relevant requests and configure the interceptor.

(\*) If your browser is not recognized by ZAP (OWASP Zed Attack Proxy), here are some solutions you can try:

Check for "Manual Explore" within the QuickStart Menu.

<figure><img src="../../../../.gitbook/assets/Manual Explore HTTP Proxis.png" alt=""><figcaption></figcaption></figure>

This feature of ZAP allows you to launch browsers from within ZAP. The browsers are automatically configured to proxy via ZAP and ignore certificate warnings, making it much easier for people to get started with ZAP as well as for more experienced users who want to use ZAP with a variety of browsers.

You can see the information about the WebDrivers in the following path: tools/ options/ selenium.

When you select "Launch Browser" the following image will be launched in your selected browser.

<figure><img src="../../../../.gitbook/assets/http proxies part 3 bis bis.png" alt=""><figcaption></figcaption></figure>

If you are having issues, we recommend you see the video posted by ZAP: [https://www.zaproxy.org/blog/2017-08-22-zap-browser-launch/](https://www.zaproxy.org/blog/2017-08-22-zap-browser-launch/)
