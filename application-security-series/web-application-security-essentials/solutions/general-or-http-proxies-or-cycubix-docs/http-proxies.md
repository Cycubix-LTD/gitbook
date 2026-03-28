---
description: As part of our Web Application Security Essentials course we offer practical guides on HTTPS proxy. Learn HTTPS proxy basics with our security essentials guide.
title: "General | HTTP Proxies (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "General | HTTP Proxies | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Proxies (1) | Cycubix Docs

## What’s a HTTP Proxy <a href="#whats_a_http_proxy" id="whats_a_http_proxy"></a>

A proxy is some forwarder application that connects your http client to backend resources. HTTP clients can be browsers, or applications like curl, SOAP UI, Postman, etc. Usually these proxies are used for routing and getting access to internet when there is no direct connection to internet from the client itself. HTTP proxies are therefore also ideal when you are testing your application. You can always use the proxy log records to see what was actually sent from client to server. So you can check the request and response headers and the XML, JSON or other payload.

HTTP Proxies receive requests from a client and relay them. They also typically record them. They act as a man-in-the-middle. It even works fine with or without HTTPS as long as your client or browser trusts the certificate of the HTTP Proxy.

### ZAP Proxy Capabilities <a href="#zap_proxy_capabilities" id="zap_proxy_capabilities"></a>

With ZAP you can record traffic, inspect traffic, modify requests and response from and to your browser, and get reports on a range of known vulnerabilities that are detected by ZAP through the inspection of the traffic. The passive and active reporting on security issues is usually used in Continuous Delivery pipelines that use a GUI-less ZAP. Here we will use ZAP interactively and mainly to see and modify requests in order to find vulnerabilities and solve assignments. ZAP has a graphical user interface, but now also has a HUD Heads-On-Display which uses a websocket connection between the browser and the ZAP proxy.
