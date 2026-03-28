---
title: "A10:2021 | Server Side Request Forgery (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "A10:2021 | Client Side Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery (1) | Cycubix Docs

### Concept <a href="#concept" id="concept"></a>

In a Server-Side Request Forgery (SSRF) attack, the attacker can abuse functionality on the server to read or update internal resources. 

The attacker can supply or modify a URL which the code running on the server will read or submit data to. Moreover, by carefully selecting the URLs, the attacker may read server configuration such as AWS metadata, connect to internal services like HTTP enabled databases, or perform post requests towards internal services that are not intended to be exposed.

### Goals <a href="#goals" id="goals"></a>

In the exercises on the following pages, you need to examine what the browser sends to the server and adjust the request to get other things from the server.

### SSRF How-To <a href="#ssrf_how_to" id="ssrf_how_to"></a>

* [https://www.hackerone.com/blog-How-To-Server-Side-Request-Forgery-SSRF](https://www.hackerone.com/blog-How-To-Server-Side-Request-Forgery-SSRF)

### A New Era of SSRF by Orange Tsai <a href="#a_new_era_of_ssrf_by_orange_tsai" id="a_new_era_of_ssrf_by_orange_tsai"></a>

[https://youtu.be/D1S-G8rJrEk](https://youtu.be/D1S-G8rJrEk)
