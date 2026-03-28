---
title: "A3:2021 | Path Transversal (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Path Transversal (2) | Cycubix Docs

#### Path traversal while uploading files <a href="#path_traversal_while_uploading_files" id="path_traversal_while_uploading_files"></a>

In this assignment, the goal is to overwrite a specific file on the file system. Of course, WebGoat cares about the users so you need to upload your file to the following location outside the usual upload location. 

<figure><img src="../../../../../.gitbook/assets/path transversal 2.png" alt=""><figcaption></figcaption></figure>

**Solution**

1. Hint: Try updating the profile WebGoat will display the location. Look at the displayed location how is the file name on the server constructed?. Does the server validate any input given in the full name field?
2. Open the interceptor with Burp or Launch Zap with the Break. 
3. Go to WebGoat, upload your file. Then go to Burp/ZAP and find the POST request. 

<figure><img src="../../../../../.gitbook/assets/profile update path transversal (1).png" alt=""><figcaption></figcaption></figure>

Request on Zap

<figure><img src="../../../../../.gitbook/assets/profile with ZAP.png" alt=""><figcaption></figcaption></figure>

Request on Burp

<figure><img src="../../../../../.gitbook/assets/path transversal 1 (1).png" alt=""><figcaption></figcaption></figure>

* Then add "../" in front of test under full name and see the answer. 

With Zap

<figure><img src="../../../../../.gitbook/assets/OK REQUEST.png" alt=""><figcaption></figcaption></figure>

With Burp

<figure><img src="../../../../../.gitbook/assets/path transversal mitigation 2 (1).png" alt=""><figcaption><p>\</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/completed with ZAP.png" alt=""><figcaption></figcaption></figure>







