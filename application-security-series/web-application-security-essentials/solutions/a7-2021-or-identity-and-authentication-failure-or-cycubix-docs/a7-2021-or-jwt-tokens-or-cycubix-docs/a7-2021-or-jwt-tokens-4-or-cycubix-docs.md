---
title: "A7: 2021 | JWT Tokens (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (4) | Cycubix Docs

### Decoding a JWT token <a href="#decoding_a_jwt_token" id="decoding_a_jwt_token"></a>

Let’s try decoding a JWT token, for this you can use the [JWT](http://127.0.0.1:9090/WebWolf/jwt) functionality inside WebWolf. Given the following token:

```
eyJhbGciOiJIUzI1NiJ9.ew0KICAiYXV0aG9yaXRpZXMiIDogWyAiUk9MRV9BRE1JTiIsICJST0xFX1VTRVIiIF0sDQogICJjbGllbnRfaWQiIDogIm15LWNsaWVudC13aXRoLXNlY3JldCIsDQogICJleHAiIDogMTYwNzA5OTYwOCwNCiAgImp0aSIgOiAiOWJjOTJhNDQtMGIxYS00YzVlLWJlNzAtZGE1MjA3NWI5YTg0IiwNCiAgInNjb3BlIiA6IFsgInJlYWQiLCAid3JpdGUiIF0sDQogICJ1c2VyX25hbWUiIDogInVzZXIiDQp9.9lYaULTuoIDJ86-zKDSntJQyHPpJ2mZAbnWRfel99iI
```

Copy and paste the following token and decode the token, can you find the user inside the token?



**Solution**

* The exercise require us to use the JWT functionality within WebWolf. We could also use [JWT](https://jwt.io/)
* Copy the given token, and open WebWolf. Go into the JWT tab. Paste the token. 

 

<figure><img src="../../../../../.gitbook/assets/use jwt webwolf.png" alt=""><figcaption></figcaption></figure>

* Copy user name and paste it on WebGoat exercise. 

<figure><img src="../../../../../.gitbook/assets/jwt user .png" alt=""><figcaption></figcaption></figure>
