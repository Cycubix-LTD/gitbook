---
title: "A2:2021 | Crypto Basics (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A2:2021 | Cryptographic Failures | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A2:2021 | Crypto Basics (3) | Cycubix Docs

### Other Encoding <a href="#other_encoding" id="other_encoding"></a>

Also other encodings are used.

#### URL encoding <a href="#url_encoding" id="url_encoding"></a>

URL encoding is used a lot when sending form data and request parameters to the server. Since spaces are not allowed in a URL, this is then replaced by %20. Similar replacements are made for other characters.

#### HTML encoding <a href="#html_encoding" id="html_encoding"></a>

HTML encoding ensures that text is displayed as-is in the browser and not interpreted by the browser as HTML.

#### UUEncode <a href="#uuencode" id="uuencode"></a>

The Unix-2-Unix encoding has been used to send email attachments.

#### XOR encoding <a href="#xor_encoding" id="xor_encoding"></a>

Sometimes encoding is used as a first and simple obfuscation technique for storing passwords. IBM WebSphere Application Server e.g. uses a specific implementation of XOR encoding to store passwords in configuration files. IBM recommends to protect access to these files and to replace the default XOR encoding by your own custom encryption. However when these recommendations are not followed, these defaults can become a vulnerability.

### Assignment <a href="#assignment" id="assignment"></a>

Now let’s see if you are able to find out the original password from this default XOR encoded string.

<figure><img src="../../../../.gitbook/assets/other encoding (1).png" alt=""><figcaption></figcaption></figure>

**Solution**

* As provided the password encoded, we will use XOR encoding to find the password. 
* We can use the following XOR decoder: [https://strelitzia.net/wasXORdecoder/wasXORdecoder.html](https://strelitzia.net/wasXORdecoder/wasXORdecoder.html)

<figure><img src="../../../../.gitbook/assets/xor encoder.png" alt=""><figcaption></figcaption></figure>

* Introduce the actual password on WebGoat. 

<figure><img src="../../../../.gitbook/assets/xor encoder 2.png" alt=""><figcaption></figcaption></figure>
