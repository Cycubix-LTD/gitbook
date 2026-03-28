---
description: Learn the basics of how to handle an HTTP requests and proxies as well as how to use developers tools for our web application security essentials course. Read now.
title: "General | HTTP Basics (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "General | HTTP Basics | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Basics (1) | Cycubix Docs

## Concept <a href="#concept" id="concept"></a>

This lesson presents the basics for understanding the transfer of data between the browser and the web application and how to trap a request/response with a HTTP proxy.

## Goals <a href="#goals" id="goals"></a>

The user should become familiar with the features of WebGoat by manipulating the above buttons to view hints, show the HTTP request parameters, the HTTP request cookies, and the Java source code. You may also try using [Zed Attack Proxy](https://www.zaproxy.org/) for the first time.

## How HTTP works: <a href="#how_http_works" id="how_http_works"></a>

All HTTP transactions follow the same general format. Each client request and server response has three parts: 

1. the request or response line;
2. a header section; 
3. the entity body.

The client initiates a transaction as follows:

* The client contacts the server and sends a document request. A GET request can have url parameters and those parameters will be available in the web access logs.
  * **GET /index.html?param=value HTTP/1.0**
* Next, the client sends optional header information to inform the server of its configuration and the document formats it will accept.
  * **User-Agent: Mozilla/4.06 Accept: image/gif,image/jpeg, /**
* In a POST request, the user supplied data will follow the optional headers and is not part of the contained within the POST URL.

About HTTP request methods: 

* **GET:** Retrieves data from the server at the specified resource URL without making any changes.
* **POST:** Submits data to be processed to the server at the specified resource URL, often resulting in a change in server state or side effects.

## Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
