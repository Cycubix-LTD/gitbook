---
title: "A3:2021 | Path Transversal (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Path Transversal (7) | Cycubix Docs

**ZIP SLIP ASSIGNMENT**

This time the developers only allow you to upload zip files. However, they made a programming mistake in uploading the zip file will extract it, but it will not replace your image. Can you find a way to overwrite your current image bypassing the programming mistake?

To make the assignment a bit easier below you will find the location of the profile image you need to replace:

<figure><img src="../../../../../.gitbook/assets/path transversal 7.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Go to the following page to find the solution. 
* Hint: Try uploading a picture in a zip file. Upload a zip file which traverses to the right directory. Did you create a zip file with the right image name?. Check the http request to find out which image name should be used. 
* When you try to upload a zip file this is the response you will get: 

<figure><img src="../../../../../.gitbook/assets/the file extracted failed.png" alt=""><figcaption></figcaption></figure>

* To find the solution, you will need to understand how to prevent path transversal vulnerabilities when handling zip files.The vulnerability allows attackers to craft zip files that, when extracted, can overwrite files outside the intended directory. Ensure that the extraction code correctly handles and validates file paths to prevent path traversal attacks.

