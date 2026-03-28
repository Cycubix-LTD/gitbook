---
title: "A3:2021 | Path Transversal (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Path Transversal (4) | Cycubix Docs

#### Path traversal while uploading files <a href="#path_traversal_while_uploading_files" id="path_traversal_while_uploading_files"></a>

The developer again became aware of the vulnerability by not validating the input of the `full name` input field. A fix was applied in an attempt to solve this vulnerability.

Again the same assignment, but can you bypass the implemented fix?

<figure><img src="../../../../../.gitbook/assets/path transversal 4.png" alt=""><figcaption></figcaption></figure>

**Solution with ZAP**

* Hints: Take a look what happened to the file name. Can we still manipulate the request?. You can try to use a proxy to intercept the POST request. Try updating the profile WebGoat will display the location. 
* We will have to see then how we can bypass the implemented fix. In this case by adding the already known pattern from the previous exercises ../ we can find a way to bypass the fix. 

<figure><img src="../../../../../.gitbook/assets/content file name.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/solved.png" alt=""><figcaption></figcaption></figure>

**Solution with BURP**

* Hint: Take a look what happened to the file name. You can try to use a proxy to intercept the POST request. 
* Open the Interceptor on Burp and find the POST request. You will see that the file name used to write the image to the disk is taken directly from the name of the file passed to the webapp. In this case is xss 2.png

<figure><img src="../../../../../.gitbook/assets/path transversal fix1.png" alt=""><figcaption></figcaption></figure>

* We can manipulate the request by adding ../ in front of the file name. 

<figure><img src="../../../../../.gitbook/assets/path transversal test 5.png" alt=""><figcaption></figcaption></figure>
