---
title: "A7: 2021 | JWT Tokens (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (5) | Cycubix Docs

### Authentication and getting a JWT token <a href="#authentication_and_getting_a_jwt_token" id="authentication_and_getting_a_jwt_token"></a>

A basic sequence of getting a token is as follows:

<figure><img src="../../../../../.gitbook/assets/authentication token.png" alt=""><figcaption></figcaption></figure>

In this flow, you can see the user logs in with a username and password on successful authentication the server returns. The server creates a new token and returns this one to the client. When the client makes a successive call toward the server it attaches the new token in the "Authorization" header. The server reads the token and first validates the signature after a successful verification the server uses the information in the token to identify the user.

#### Claims <a href="#claims" id="claims"></a>

The token contains claims to identify the user and all other information necessary for the server to fulfill the request. Be aware not to store sensitive information in the token and always send it over a secure channel.
