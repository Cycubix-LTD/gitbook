---
title: "A3:2021 | Path Transversal (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Path Transversal (3) | Cycubix Docs

#### Path traversal while uploading files <a href="#path_traversal_while_uploading_files" id="path_traversal_while_uploading_files"></a>

The developer became aware of the vulnerability and implemented a fix that removed the `../` from the input. Again the same assignment, but can you bypass the implemented fix?

<figure><img src="../../../../../.gitbook/assets/path transversal 3.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Just like in the previous lab, we will upload an image and intercept the request with ZAP or Burp. 
* Once we intercept it we analyze the POST request and we think how to bypass it. One of the hints says "The new and improved version removes `../` from the input, can you bypass this?". 
*   We will try to bypass it with 



    ```
    ....//test
    ```
* Now check the response on Zap. 

<figure><img src="../../../../../.gitbook/assets/post request path.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/ok request 2 (1).png" alt=""><figcaption></figcaption></figure>



