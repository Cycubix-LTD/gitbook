---
title: "A7: 2021 | JWT Tokens (12) | Cycubix Docs"
layout: default
nav_order: 12
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (12) | Cycubix Docs

### Refreshing a token <a href="#refreshing_a_token" id="refreshing_a_token"></a>

#### Introduction <a href="#introduction" id="introduction"></a>

In this section we touch upon refreshing an access token.

#### Types of tokens <a href="#types_of_tokens" id="types_of_tokens"></a>

In general there are two types of tokens: an access token and a refresh token. The access token is used for making API calls towards the server. Access tokens have a limited life span, that’s where the refresh token comes in. Once the access token is no longer valid a request can be made towards the server to get a new access token by presenting the refresh token. The refresh token can expire but their life span is much longer. This solves the problem of a user having to authenticate again with their credentials. Whether you should use a refresh token and an access token depends, below can find a couple of points to keep in mind while choosing which tokens to use.

So a normal flow can look like:

```
curl -X POST -H -d 'username=webgoat&password=webgoat' localhost:8080/WebGoat/login
```

The server returns:

```
{
    "token_type":"bearer",
    "access_token":"XXXX.YYYY.ZZZZ",
    "expires_in":10,
    "refresh_token":"4a9a0b1eac1a34201b3c5659944e8b7"
}
```

As you can see the refresh token is a random string which the server can keep track of (in memory or store in a database) in order to match the refresh token to the user the refresh token was granted to. So in this case whenever the access token is still valid we can speak of a "stateless" session, there is no burden on the server side to setup the user session, the token is self contained. When the access token is no longer valid the server needs to query for the stored refresh token to make sure the token is not blocked in any way.

Whenever the attacker gets a hold on an access token it is only valid for a certain amount of time (say 10 minutes). The attacker then needs the refresh token to get a new access token. That is why the refresh token needs better protection. It is also possible to make the refresh token stateless but this means it will become more difficult to see if the user revoked the tokens. After the server made all the validations it must return a new refresh token and a new access token to the client. The client can use the new access token to make the API call.

#### What should you check for? <a href="#what_should_you_check_for" id="what_should_you_check_for"></a>

Regardless of the chosen solution you should store enough information on the server side to validate whether the user is still trusted. You can think of many things, like store the ip address, keep track of how many times the refresh token is used (using the refresh token multiple times in the valid time window of the access token might indicate strange behavior, you can revoke all the tokens and let the user authenticate again). Also keep track of which access token belonged to which refresh token otherwise an attacker might be able to get a new access token for a different user with the refresh token of the attacker (see [https://emtunc.org/blog/11/2017/jwt-refresh-token-manipulation/](https://emtunc.org/blog/11/2017/jwt-refresh-token-manipulation/) for a nice write up about how this attack works) Also a good thing to check for is the ip address or geolocation of the user. If you need to give out a new token check whether the location is still the same if not revoke all the tokens and let the user authenticate again.

#### Need for refresh tokens <a href="#need_for_refresh_tokens" id="need_for_refresh_tokens"></a>

Does it make sense to use a refresh token in a modern single page application (SPA)? As we have seen in the section about storing tokens there are two options: web storage or a cookie which mean a refresh token is right beside an access token, so if the access token is leaked chances are the refresh token will also be compromised. Most of the time there is a difference of course. The access token is sent when you make an API call, the refresh token is only sent when a new access token should be obtained, which in most cases is a different endpoint. If you end up on the same server you can choose to only use the access token.

As stated above using an access token and a separate refresh token gives some leverage for the server not to check the access token over and over. Only perform the check when the user needs a new access token. It is certainly possible to only use an access token. At the server you store the exact same information you would store for a refresh token, see previous paragraph. This way you need to check the token each time but this might be suitable depending on the application. In the case the refresh tokens are stored for validation it is important to protect these tokens as well (at least use a hash function to store them in your database).

#### JWT a good idea? <a href="#jwt_a_good_idea" id="jwt_a_good_idea"></a>

There are a lot of resources available which question the usecase for using JWT token for client to server authentication with regards to cookies. The best place to use a JWT token is between server to server communication. In a normal web application you are better of using plain old cookies. See for more information:

Links provided by WebGoat are not under HTTPS support. 

* [stop-using-jwt-for-sessions](http://cryto.net/~joepie91/blog/2016/06/13/stop-using-jwt-for-sessions/)
* [stop-using-jwt-for-sessions-part-2-why-your-solution-doesnt-work](http://cryto.net/~joepie91/blog/2016/06/19/stop-using-jwt-for-sessions-part-2-why-your-solution-doesnt-work/) (link does not have HTTPS support)
* [flowchart](http://cryto.net/~joepie91/blog/attachments/jwt-flowchart.png)
