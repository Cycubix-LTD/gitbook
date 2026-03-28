---
title: "A7: 2021 | JWT Tokens (19) | Cycubix Docs"
layout: default
nav_order: 19
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (19) | Cycubix Docs

#### Best practices <a href="#best_practices" id="best_practices"></a>

Some best practices when working with JWT:

* Fix the algorithm, do not allow a client to switch the algorithm.
* Make sure you use an appropriate key length when using a symmetric key for signing the token.
* Make sure the claims added to the token do not contain personal information. If you need to add more information opt for encrypting the token as well.
* Add sufficient test cases to your project to verify invalid tokens actually do not work. Integration with a third party to check your token does not mean you do not have test your application at all.
* Take a look at the best practices mentioned in [https://tools.ietf.org/html/rfc8725#section-2](https://tools.ietf.org/html/rfc8725#section-2)
