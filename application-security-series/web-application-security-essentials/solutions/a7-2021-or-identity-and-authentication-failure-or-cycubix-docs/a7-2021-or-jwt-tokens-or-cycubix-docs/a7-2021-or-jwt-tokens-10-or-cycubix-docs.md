---
title: "A7: 2021 | JWT Tokens (10) | Cycubix Docs"
layout: default
nav_order: 10
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (10) | Cycubix Docs

#### Solution <a href="#solution" id="solution"></a>

In the past assignments we learned to **NOT** trust the libraries to do the correct thing for us. In both cases we saw that even specifying the JWT key and passing the correct algorithm. Even using the token:

```
eyJhbGciOiJIUzI1NiJ9.ew0KICAiYWRtaW4iIDogdHJ1ZSwNCiAgImlhdCIgOiAxNTE2MjM5MDIyLA0KICAic3ViIiA6ICIxMjM0NTY3ODkwIiwNCiAgInVzZXIiIDogIkpvaG4gRG9lIg0KfQ.

{
  "alg" : "HS256"
},
{
  "admin" : true,
  "iat" : 1516239022,
  "sub" : "1234567890",
  "user" : "John Doe"
}
```

And the following Java code:

```
Jwt jwt = Jwts.parser().setSigningKey(JWT_PASSWORD).parse(accessToken);
```

You see we set the signing key with `setSigningKey` the library still skips the validation of the signature.

It is not only limited to the traditional `alg: none` attack, but it also works with the `alg: HS256`.

#### Conclusion <a href="#conclusion" id="conclusion"></a>

When you have chosen a library to help dealing with JWT tokens make sure to:

* use the correct method in your code when validating tokens.
* add test cases and validate the algorithm confusion is not possible.
* as a security team write a utility methods to be used by the teams which encapsulate the library to make sure the teams use the correct parsing logic.

#### Alternative: Paseto <a href="#alternative_paseto" id="alternative_paseto"></a>

The algorithm confusion is a real problem when dealing with JWTs it can be avoided by using PASETO (**P**latform-**A**gnostic **SE**curity **TO**kens), which is currently implemented in 10 programming languages. One of the drawbacks of using this method is that JWT is widely spread for example think about using OAuth, so it might not be the best solution to use.

For more information take a look at the following video: 

[https://youtu.be/RijGNytjbOI](https://youtu.be/RijGNytjbOI)

