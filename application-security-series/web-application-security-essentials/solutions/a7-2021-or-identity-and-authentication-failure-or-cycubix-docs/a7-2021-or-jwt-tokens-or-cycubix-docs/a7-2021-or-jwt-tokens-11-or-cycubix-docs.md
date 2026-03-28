---
title: "A7: 2021 | JWT Tokens (11) | Cycubix Docs"
layout: default
nav_order: 11
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (11) | Cycubix Docs

### JWT cracking <a href="#jwt_cracking" id="jwt_cracking"></a>

With the HMAC with SHA-2 Functions you use a secret key to sign and verify the token. Once we figure out this key we can create a new token and sign it. So it is very important the key is strong enough so a brute force or dictionary attack is not feasible. Once you have a token you can start an offline brute force or dictionary attack.

#### Assignment <a href="#assignment" id="assignment"></a>

Given we have the following token try to find out secret key and submit a new key with the username changed to WebGoat.<br>

### JWT cracking <a href="#jwt_cracking" id="jwt_cracking"></a>

With the HMAC with SHA-2 Functions you use a secret key to sign and verify the token. Once we figure out this key we can create a new token and sign it. So it is very important the key is strong enough so a brute force or dictionary attack is not feasible. Once you have a token you can start an offline brute force or dictionary attack.

#### Assignment <a href="#assignment" id="assignment"></a>

Given we have the following token try to find out secret key and submit a new key with the username changed to WebGoat.

```
eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJXZWJHb2F0IFRva2VuIEJ1aWxkZXIiLCJhdWQiOiJ3ZWJnb2F0Lm9yZyIsImlhdCI6MTcxODQ4MzczNiwiZXhwIjoxNzE4NDgzNzk2LCJzdWIiOiJ0b21Ad2ViZ29hdC5vcmciLCJ1c2VybmFtZSI6IlRvbSIsIkVtYWlsIjoidG9tQHdlYmdvYXQub3JnIiwiUm9sZSI6WyJNYW5hZ2VyIiwiUHJvamVjdCBBZG1pbmlzdHJhdG9yIl19.NFhW9WsFihm7R7Gxi8YXUnOGfUedtJGUYXFJO8Rc35Q

```

<figure><img src="../../../../../.gitbook/assets/submit token 11.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Save the token and try to verify the token locally. 
* Download a word list dictionary (https://github.com/first20hours/google-10000-english). 
* Write a small program or use HashCat for brute forcing the token according the word list. 
* You can access the source code for the lesson in the followin link: [WebGoat Secret Key](https://github.com/WebGoat/WebGoat/blob/main/src/test/java/org/owasp/webgoat/lessons/jwt/JWTSecretKeyEndpointTest.java) .
* Click the submit button on WebGoat and find the POST request in ZAP. 
* Go into [https://jwt.io/](https://jwt.io/), and paste the entire token. Examine the payload data. 
* Copy the claims part (payloads data) of the token and go to tools in ZAP/decoder, to decode that section of the token into base64. 

<figure><img src="../../../../../.gitbook/assets/DECODE BASE64.png" alt=""><figcaption></figcaption></figure>

* Copy the payload details into the payload section at JWT page. 
* Go ahead and change sub, username and email into WebGoat. 
* It's very important to change the expiration time of the token. 
* We will also need the secret to unlock the valid signature. For that we will save the key that we have, and use the HASHCAT command

