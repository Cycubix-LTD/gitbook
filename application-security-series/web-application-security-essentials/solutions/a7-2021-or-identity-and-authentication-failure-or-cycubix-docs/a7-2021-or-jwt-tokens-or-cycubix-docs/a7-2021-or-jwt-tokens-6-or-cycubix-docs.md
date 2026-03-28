---
title: "A7: 2021 | JWT Tokens (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (6) | Cycubix Docs

### JWT signing <a href="#jwt_signing" id="jwt_signing"></a>

Each JWT token should at least be signed before sending it to a client, if a token is not signed the client application would be able to change the contents of the token. The signing specifications are defined [here](https://tools.ietf.org/html/rfc7515) the specific algorithms you can use are described [here](https://tools.ietf.org/html/rfc7518). 

It basically comes down you use "HMAC with SHA-2 Functions" or "Digital Signature with RSASSA-PKCS1-v1\_5/ECDSA/RSASSA-PSS" function for signing the token.

#### Checking the signature <a href="#checking_the_signature" id="checking_the_signature"></a>

One important step is to **verify the signature** before performing any other action, let’s try to see some things you need to be aware of before validating the token.

### Assignment <a href="#assignment" id="assignment"></a>

Try to change the token you receive and become an admin user by changing the token and once you are admin reset the votes. 

<figure><img src="../../../../../.gitbook/assets/vote your favorite.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Select a different user and look at the token you receive back, use the delete button to reset the votes count. Change user "guest" to "Tom". 
* Try to reset the votes and this message will appear "Only an admin user can reset the votes". 
* Turn on the interceptor (Burp) or Break (ZAP) and search for the POST request when you try again to reset the votes. Send the request to the Repeater or Manual Request Editor, depending if you are using Burp or ZAP. 
* Remember that a token is base64 encoded and consists of three parts: header, claims and signature. Try to identify the header on the token. 
* For example: access\_token=eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE3MTkzNDU3NTcsImFkbWluIjoiZmFsc2UiLCJ1c2VyIjoiVG9tIn0.oabZmZWfUYiR0aRB8nTBQI23VM4vGNtWSJWbTH71BOqNns\_icMhlBWa2oV1n78EBXtTQLQTvky\_Lh-9cJSrxcg
* eyJhbGciOiJIUzUxMiJ9 is the Header. Send it to the decoder and decode as base64. 

<figure><img src="../../../../../.gitbook/assets/header decoded.png" alt=""><figcaption></figcaption></figure>

* The retrieved response is algorithm HS512. Change it to alg: none. 

<figure><img src="../../../../../.gitbook/assets/alg none.png" alt=""><figcaption></figcaption></figure>

* Now, encode "none" into base64. 

<figure><img src="../../../../../.gitbook/assets/encode as base 64.png" alt=""><figcaption></figcaption></figure>

* Change the header in the access token in the repeater. After, select the claims an send it to the decoder. In this case the value will be: eyJpYXQiOjE3MTkzNDU3NTcsImFkbWluIjoiZmFsc2UiLCJ1c2VyIjoiVG9tIn0
* Decode it into base64. And change "admin":"false" into "admin":"true". This change will modify the payload. 

<figure><img src="../../../../../.gitbook/assets/true tom.png" alt=""><figcaption></figcaption></figure>

* Now encode it into base64. 

<figure><img src="../../../../../.gitbook/assets/encode into base 64.png" alt=""><figcaption></figcaption></figure>

* Replace the claims in the repeater. 
* In the repeater remove the signatures segment and send the request. 

You will see the following message: 

<figure><img src="../../../../../.gitbook/assets/a4 a7 solved.png" alt=""><figcaption></figcaption></figure>

* You can use that new Access Token in the Proxy request. 
