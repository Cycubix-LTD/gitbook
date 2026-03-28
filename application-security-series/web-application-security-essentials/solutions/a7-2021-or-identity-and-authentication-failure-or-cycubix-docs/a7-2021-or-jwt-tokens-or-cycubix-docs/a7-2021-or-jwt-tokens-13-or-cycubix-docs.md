---
title: "A7: 2021 | JWT Tokens (13) | Cycubix Docs"
layout: default
nav_order: 13
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (13) | Cycubix Docs

### Refreshing a token <a href="#refreshing_a_token" id="refreshing_a_token"></a>

It is important to implement a good strategy for refreshing an access token. This assignment is based on a vulnerability found in a private bug bounty program on Bugcrowd, you can read the full write up [here](https://emtunc.org/blog/11/2017/jwt-refresh-token-manipulation/)

#### Assignment <a href="#assignment" id="assignment"></a>

From a breach of last year the following logfile is available [here](http://localhost:8080/WebGoat/images/logs.txt) Can you find a way to order the books but let **Tom** pay for them?

<figure><img src="../../../../../.gitbook/assets/REFRESHING AA TOKEN.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Hints: Look at the access log you will find a token there. The token from the access log is no longer valid, can you find a way to refresh it?. The endpoint for refreshing a token is 'JWT/refresh/newToken'. Use the found access token in the Authorization: Bearer header and use your own refresh toke&#x6E;**.** 
* Intercept the post request with ZAP after you hit the chekout request. 
* Send the request to the request editor.  See Jerry's past credentials. 

<figure><img src="../../../../../.gitbook/assets/request credentials.png" alt=""><figcaption></figcaption></figure>

* Open the logfile to find the session information. 

<figure><img src="../../../../../.gitbook/assets/log file.png" alt=""><figcaption></figcaption></figure>

*   Check the checkout token: 

    ```
    /refresh/checkout?token=eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE1MjYxMzE0MTEsImV4cCI6MTUyNjIxNzgxMSwiYWRtaW4iOiJmYWxzZSIsInVzZXIiOiJUb20ifQ.DCoaq9zQkyDH25EcVWKcdbyVfUL4c9D4jRvsqOqvi9iAd4QuqmKcchfbU8FNzeBNF9tLeFXHZLU4yRkq-bjm7Q 
    ```
* Other way to find the token is by intercepting the POST request with ZAP. 

<figure><img src="../../../../../.gitbook/assets/token zap.png" alt=""><figcaption></figcaption></figure>

* Also, you can see that the response says user is Jerry not Tom. 

<figure><img src="../../../../../.gitbook/assets/Jerry not Tom.png" alt=""><figcaption></figcaption></figure>

* Insert the checkout token into [https://jwt.io/](https://jwt.io/). 
* We will need to change the header and payload to validate a new token. So we will need to ask for an access token renewal using “Tom” access token present in the given log and “Jerry” refresh token obtained by loading the lesson page. 
* Copy the header and open the decoder in Zap from the tools tab. Paste the header and decode it into base64. Then change it into "alg:none" and encode it again into base 64. 
* Paste the result into the header of the token in JWT and check that effectively the header refers to alg=none. 
* Now go ahead and paste the claims in the payload into the decoder in Zap. Decode it into base64. Then copy that value, change the values into "Tom" and "True" and encode it in base64. 
* Once you have your header and payload paste it in the POST request in ZAP. Leave the signature blank. 
* Below you can see the changed token. 

<figure><img src="../../../../../.gitbook/assets/changed token.png" alt=""><figcaption></figcaption></figure>

* Check the response: 

<figure><img src="../../../../../.gitbook/assets/renew token.png" alt=""><figcaption></figcaption></figure>
