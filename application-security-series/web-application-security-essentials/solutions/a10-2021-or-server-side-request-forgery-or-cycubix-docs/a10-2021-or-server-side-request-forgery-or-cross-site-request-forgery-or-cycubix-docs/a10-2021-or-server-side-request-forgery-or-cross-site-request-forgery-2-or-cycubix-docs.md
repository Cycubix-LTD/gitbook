---
title: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (2) | Cycubix Docs

### CSRF with a GET request <a href="#csrf_with_a_get_request" id="csrf_with_a_get_request"></a>

This is the most simple CSRF attack to perform. For example you receive an e-mail with the following content:

`<a href="http://bank.com/transfer?account_number_from=123456789&account_number_to=987654321&amount=100000">View my Pictures!</a>`

If the user is still logged in to the website of bank.com this simple GET request will transfer money from one account to another. Of course in most cases the website might have multiple controls to approve the request.
