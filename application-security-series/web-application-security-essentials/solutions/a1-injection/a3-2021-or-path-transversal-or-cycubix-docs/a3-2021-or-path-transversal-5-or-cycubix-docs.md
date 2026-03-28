---
title: "A3:2021 | Path Transversal (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Path Transversal (5) | Cycubix Docs

**Retrieving other files with a path traversal**

Path traversals are not limited to file uploads; when retrieving files, it can be the case that a path traversal is possible to retrieve other files from the system. In this assignment, try to find a file called `path-traversal-secret.jpg`

<figure><img src="../../../../../.gitbook/assets/path transversal 5.png" alt=""><figcaption></figcaption></figure>



**Solution**

* Hint: Can you specify the image to be fetched?. Look at the location header...Use /random?id=1 for example to fetch a specific image. Use /random/?id=../../1.jpg to navigate to a different directory. '..' and '/' are no longer allowed, can you bypass this restriction?. Use url encoding for ../ to bypass the restriction.
* Open Zap or Burp Interceptor. Then in WebGoat hit on "Show Random cat picture". 
* The request and response looks like this: 

With ZAP

<figure><img src="../../../../../.gitbook/assets/random cat picture path.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/path to cat.png" alt=""><figcaption></figcaption></figure>

*   It could happen that you see the request with the following path: 

    ```
    GET http://localhost:8080/WebGoat/images/cats HTTP/1.1
    ```

In that case, go into the developer tools and check the path. 

<figure><img src="../../../../../.gitbook/assets/developer tools random picture path.png" alt=""><figcaption></figcaption></figure>

* In that case, find the request the correct request. 
* See if you can edit the request according to this path to see if we can manipulate the request: 

```
/PathTraversal/random-picture?id=../../
```

<figure><img src="../../../../../.gitbook/assets/new path.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/illegal characters.png" alt=""><figcaption></figcaption></figure>

* Since ../ is illegal, we can try to encode it as URL with ZAP decoder. In the case of ZAP, to decode you need to go to Tools/Encode-Decode-Hash. 

Example in Zap Decoder

<figure><img src="../../../../../.gitbook/assets/zap path transversal decoded.png" alt=""><figcaption></figcaption></figure>

* We then replace the encoded value with an alternative encoded value for id=%2e%2e%2f%2e%2e%2fpath-transversal-secret
* The system could now process the request. 

<figure><img src="../../../../../.gitbook/assets/path transversal secret ok.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/response path transversal secret.png" alt=""><figcaption></figcaption></figure>

* We have now find the path to the files. Let's go ahead and find the file provided in the exercise "path-traversal-secret.jpg". Change the request. 

<figure><img src="../../../../../.gitbook/assets/path transversal secret yes.png" alt=""><figcaption></figcaption></figure>

* See the answer. Make sure you selected "text" in the body request. If not you will not see the reply. 

<figure><img src="../../../../../.gitbook/assets/secret sha (1).png" alt=""><figcaption></figcaption></figure>

* Getting your SHA-512

Go to [https://sha512.online/](https://sha512.online/) and imput a string with your username for WebGoat. 

It will generate a HASH. Submit the secret answer. 

<figure><img src="../../../../../.gitbook/assets/submit secret answer.png" alt=""><figcaption></figcaption></figure>

