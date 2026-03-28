---
title: "A7: 2021 | JWT Tokens (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (2) | Cycubix Docs

### Structure of a JWT token <a href="#structure_of_a_jwt_token" id="structure_of_a_jwt_token"></a>

Let’s take a look at the structure of a JWT token:

<figure><img src="../../../../../.gitbook/assets/jwt token 2.png" alt=""><figcaption></figcaption></figure>

The token is base64 encoded and consists of three parts:

* header
* claims
* signature

Both header and claims consist are represented by a JSON object. The header describes the cryptographic operations applied to the JWT and optionally, additional properties of the JWT. The claims represent a JSON object whose members are the claims conveyed by the JWT.
