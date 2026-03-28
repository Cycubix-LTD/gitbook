---
title: "A2:2021 | Crypto Basics (2)  | Cycubix Docs"
layout: default
nav_order: 2
parent: "A2:2021 | Cryptographic Failures | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A2:2021 | Crypto Basics (2)  | Cycubix Docs

### Base64 Encoding <a href="#base64_encoding" id="base64_encoding"></a>

Encoding is not really cryptography, but it is used a lot in all kinds of standards around cryptographic functions. Especially Base64 encoding.

Encoding is is the process of converting data from one form to another. This process is typically used to ensure data is in a suitable format for transmission, storage, or processing. Decoding is the reverse process of encoding. It converts encoded data back into its original form.

Base64 encoding is a technique used to transform all kinds of bytes to a specific range of bytes. This specific range is the ASCII readable bytes. This way you can transfer binary data such as secret or private keys more easily. You could even print these out or write them down. Encoding is also reversible. So if you have the encoded version, you can create the original version.

On wikipedia you can find more details. Basically it goes through all the bytes and transforms each set of 6 bits into a readable byte (8 bits). The result is that the size of the encoded bytes is increased with about 33%.

```
Hello ==> SGVsbG8=
0x4d 0x61 ==> TWE=
```

#### Basic Authentication <a href="#basic_authentication" id="basic_authentication"></a>

Basic authentication is sometimes used by web applications. This uses base64 encoding. Therefore, it is important to at least use Transport Layer Security (TLS or more commonly known as https) to protect others from reading the username password that is sent to the server.

```
$echo -n "myuser:mypassword" | base64
bXl1c2VyOm15cGFzc3dvcmQ=
```

The HTTP header will look like:

```
Authorization: Basic bXl1c2VyOm15cGFzc3dvcmQ=
```

<figure><img src="../../../../.gitbook/assets/encode 64 exercise (1).png" alt=""><figcaption></figcaption></figure>

**Solution**

* Go to [https://www.base64decode.org/](https://www.base64decode.org/) and decode the authorization header "d2ViZ29hdHRlc3Q3OnNlY3JldA==". 

<figure><img src="../../../../.gitbook/assets/crypto basics 1.png" alt=""><figcaption></figcaption></figure>

* It will decode you username and password. 
* Type those results in WebGoat. 

<figure><img src="../../../../.gitbook/assets/crypto basics 2.png" alt=""><figcaption></figcaption></figure>
