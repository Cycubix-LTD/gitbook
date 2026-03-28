---
title: "A1:2021 | Insecure Direct Object Reference (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A1:2021 | Insecure Direct Object Reference | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Insecure Direct Object Reference (6) | Cycubix Docs

### Secure Object References <a href="#secure_object_references" id="secure_object_references"></a>

#### Start with the end in mind <a href="#start_with_the_end_in_mind" id="start_with_the_end_in_mind"></a>

Do you have your access control documented? If you don’t, how can you enforce it? 

Access control is defined by the business logic that guides the application and/or privacy and other laws.

**Horizontal and Vertical Access Control**

Often times we think of access control in terms of 'roles' (user, power-user, admin, etc.). 

However, as noted in the previous exercises, users with the same 'role' can access each other’s data. This is horizontal access control. Both should be enforced. 

**Access Control Matrix**

<figure><img src="../../../../../.gitbook/assets/access control matrix.png" alt=""><figcaption></figcaption></figure>

**Audit Access**

As displayed in the above example, your access control rules should include provisions of what access is logged. 

For example, if a super-user or admin can edit other’s profiles …​ That is something that should be logged. Other examples would include detected violations or attempts to violate access control mechanisms.

#### Using Indrect References <a href="#using_indrect_references" id="using_indrect_references"></a>

Not many applications employ it, but you can use **indirect** references. In this case you can run your references across a hashing, encoding or other function on the server so that the id that the client sees is not the actual reference which the server handles. 

This will reduce efficiency some (a common trade-off for security) and is still subject to being guessed, brute-forced or reverse engineered.

This approach should not be the only protection used. It can be used as an additional layer. Your server must implement the logic of mapping client (indirect) to server (direct) references.

Secure Object References

#### Start with the end in mind <a href="#start_with_the_end_in_mind" id="start_with_the_end_in_mind"></a>

Do you have your access control documented? If you don’t, how can you enforce it? 

Access control is defined by the business logic that guides the application and/or privacy and other laws.

**Horizontal and Vertical Access Control**

Often times we think of access control in terms of 'roles' (user, power-user, admin, etc.). 

However, as noted in the previous exercises, users with the same 'role' can access each other’s data. This is horizontal access control. Both should be enforced. 

**Access Control Matrix**

<figure><img src="../../../../../.gitbook/assets/access control matrix (1).png" alt=""><figcaption></figcaption></figure>

**Audit Access**

As displayed in the above example, your access control rules should include provisions of what access is logged. 

For example, if a super-user or admin can edit other’s profiles …​ That is something that should be logged. Other examples would include detected violations or attempts to violate access control mechanisms.

#### Using Indrect References <a href="#using_indrect_references" id="using_indrect_references"></a>

Not many applications employ it, but you can use **indirect** references. In this case you can run your references across a hashing, encoding or other function on the server so that the id that the client sees is not the actual reference which the server handles. 

This will reduce efficiency some (a common trade-off for security) and is still subject to being guessed, brute-forced or reverse engineered.

This approach should not be the only protection used. It can be used as an additional layer. Your server must implement the logic of mapping client (indirect) to server (direct) references.

#### Access Control & APIs <a href="#access_control_apis" id="access_control_apis"></a>

Many time, APIs or RESTFul endpoints rely on obscurity , a static 'key', or lack of imagination on the user’s part to control access. Good options such as digitally signed JSON Web Tokens ([https://jwt.io](https://jwt.io/)) are a good option for API authentication & access control using a combination of the claims and a digital/cryptographic signature to validate the consumer. Other emerging standards such as Secure Token Binding promise a 'cryptographic state' for web services in the request headers …​[https://tools.ietf.org/html/draft-ietf-tokbind-protocol-10](https://tools.ietf.org/html/draft-ietf-tokbind-protocol-10)

[https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)

[https://tools.ietf.org/html/draft-ietf-tokbind-https-06](https://tools.ietf.org/html/draft-ietf-tokbind-https-06)
