---
title: "A1:2021 | Insecure Direct Object Reference (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "A1:2021 | Insecure Direct Object Reference | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Insecure Direct Object Reference (1) | Cycubix Docs

Direct Object References are when an application uses client-provided input to access data & objects. 

**Insecure Direct Object References (IDOR)** indicate a vulnerability that occurs when an application provides direct access to objects based on user-supplied input, and it doesn't verify the user's authorization to access those objects.

These are considered insecure when the reference is not properly handled and allows for authorization bypasses or disclose private data that could be used to perform operations or access data that the user should not be able to perform or access. Let’s say that as a user, you go to view your profile and the URL looks something like:

#### Some Examples <a href="#examples" id="examples"></a>

Examples of Direct Object References (DOR) using the GET method can include URLs where parameters directly reference objects such as files, database records, or other resources. Here are some scenarios that illustrate this concept:

#### Example 1: User Profile Access

A web application allows users to view their profile information by specifying their user ID in the URL.

```plaintext
http://example.com/profile?id=12345
```

If an attacker changes the `id` parameter to another user's ID, such as `id=12346`, and the application does not verify the user's authorization, the attacker might access someone else's profile information.

```
http://example.com/profile?id=12346
```

#### Example 2: Document Access

An application allows users to download documents by specifying the document ID in the URL.

```plaintext
http://example.com/download?documentId=789
```

If the application does not perform proper access checks, an attacker could change the `documentId` to access restricted documents.

```plaintext
http://example.com/download?documentId=790
```

#### Example 3: Order Details

An e-commerce site lets users view their order details by passing an order ID in the URL.

```plaintext
http://example.com/order?orderId=456
```

If the application does not verify that the order belongs to the logged-in user, an attacker could modify the `orderId` to view other users' orders.

```plaintext
http://example.com/order?orderId=457
```

#### Example 4: File Access

A web application allows users to view files by specifying the file name in the URL.

```plaintext
http://example.com/files?file=report.pdf
```

If the application does not restrict access to certain files, an attacker could change the `file` parameter to access sensitive files.

```plaintext
http://example.com/files?file=confidential.pdf
```

#### Other Methods <a href="#other_methods" id="other_methods"></a>

POST, PUT, DELETE or other methods are also potentially susceptible and mainly only differ in the method and the potential payload.

#### More good reading <a href="#more_good_reading" id="more_good_reading"></a>

Before we go on to practice, here’s some good reading on Insecure Direct Object References:

* [https://www.owasp.org/index.php/Testing\_for\_Insecure\_Direct\_Object\_References\_(OTG-AUTHZ-004)](https://www.owasp.org/index.php/Testing_for_Insecure_Direct_Object_References_\(OTG-AUTHZ-004\))
* [https://www.owasp.org/index.php/Top\_10-2017\_A5-Broken\_Access\_Control](https://www.owasp.org/index.php/Top_10-2017_A5-Broken_Access_Control)
* [https://www.owasp.org/index.php/Top\_10\_2013-A4-Insecure\_Direct\_Object\_References](https://www.owasp.org/index.php/Top_10_2013-A4-Insecure_Direct_Object_References)
* [http://cwe.mitre.org/data/definitions/639.html](http://cwe.mitre.org/data/definitions/639.html)

OWASP cheatsheet on IDOR visit: [https://cheatsheetseries.owasp.org/cheatsheets/Insecure\_Direct\_Object\_Reference\_Prevention\_Cheat\_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Insecure_Direct_Object_Reference_Prevention_Cheat_Sheet.html)
