---
title: "A2:2021 | Crypto Basics (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A2:2021 | Cryptographic Failures | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A2:2021 | Crypto Basics (6) | Cycubix Docs

A signature is a hash that can be used to check the validity of some data. The signature can be supplied separately from the data that it validates, or in the case of CMS or SOAP can be included in the same file. (Where parts of that file contain the data and parts contain the signature).

Signing is used when integrity is important. It is meant to be a guarantee that data sent from Party-A to Party-B was not altered. So Party-A signs the data by calculating the hash of the data and encrypting that hash using an asymmetric private key. Party-B can then verify the data by calculating the hash of the data and decrypting the signature to compare if both hashes are the same.

### RAW signatures <a href="#raw_signatures" id="raw_signatures"></a>

A raw signature is usually calculated by Party-A as follows:

* **create a hash of the data (e.g. SHA-256 hash)**
* **encrypt the hash using an asymmetric private key (e.g. RSA 2048 bit key)**
* **(optionally) encode the binary encrypted hash using base64 encoding**

Party-B will have to get the certificate with the public key as well. This might have been exchanged before. So at least 3 files are involved: the data, the signature and the certificate.

### CMS signatures <a href="#cms_signatures" id="cms_signatures"></a>

A CMS signature is a standardized way to send data + signature + certificate with the public key all in one file from Party-A to Party-B. As long as the certificate is valid and not revoked, Party-B can use the supplied public key to verify the signature.

### SOAP signatures <a href="#soap_signatures" id="soap_signatures"></a>

A SOAP signature also contains data and the signature and optionally the certificate. All in one XML payload. There are special steps involved in calculating the hash of the data. This has to do with the fact that the SOAP XML sent from system to system might introduce extra elements or timestamps. Also, SOAP Signing offers the possibility to sign different parts of the message by different parties.

### Email signatures <a href="#email_signatures" id="email_signatures"></a>

Sending emails is not very difficult. You have to fill in some data and send it to a server that forwards it, and eventually it will end up at its destination. However, it is possible to send emails with a FROM field that is not your own email address. In order to guarantee to your receiver that you really sent this email, you can sign your email. A trusted third party will check your identity and issue an email signing certificate. You install the private key in your email application and configure it to sign emails that you send out. The certificate is issued on a specific email address and all others that receive this email will see an indication that the sender is verified, because their tools will verify the signature using the public certificate that was issued by the trusted third party.

### PDF or Word or other signatures <a href="#pdf_or_word_or_other_signatures" id="pdf_or_word_or_other_signatures"></a>

Adobe PDF documents and Microsoft Word documents are also examples of things that support signing. The signature is also inside the same document as the data so there is some description on what is part of the data and what is part of the metadata. Governments usually send official documents with a PDF that contains a certificate.

### Assignment <a href="#assignment" id="assignment"></a>

Here is a simple assignment. A private RSA key is sent to you. Determine the modulus of the RSA key as a hex string, and calculate a signature for that hex string using the key. The exercise requires some experience with OpenSSL. You can search on the Internet for useful commands and/or use the HINTS button to get some tips.

<figure><img src="../../../../.gitbook/assets/signatures (1).png" alt=""><figcaption></figcaption></figure>

**Solution**

* Taking into consideration that we were given a private RSA key, we will need to download OpenSSL and save the private key into a pem file.  If you have problems installing on your Windows Open SSL, you can use a Python script to achieve the same objectives. 

**Hints**

* Use openssl to get the public key from the private key. Apparently both private and public key information are stored.
* Use the private key to sign the "modulus" value of the public key. 
* Actually the "modulus" of the public key is the same as the private key. You could use openssl rsa -in test.key -pubout > test.pub and then openssl rsa -in test.pub -pubin -modulus -noout or other components.
* Make sure that you do not take hidden characters into account. You might want to use echo -n "00AE89..." | openssl dgst -sign somekey -sha256 ... and do not forget to base64 encode the outcome. 

**Solution**

* We will use WebGoat docker container terminal to run the commands. 
* As stated in WebGoat exercise, we have the private key value. 
* In base on the information provided we can create the following echo commands: 

```
echo -----BEGIN PRIVATE KEY----- > private.key
echo _THE_PRIVATE_KEY_ >> private.key
echo -----END PRIVATE KEY----- >> private.key
```

3. To get the modulus we will need to run the following openssl command: 

```
openssl rsa -text -noout -in private.key
```

* The information regarding the modulus will be retrieved: 

<figure><img src="../../../../.gitbook/assets/modulus.png" alt=""><figcaption></figcaption></figure>

* Copy and paste the modulus information in WebGoat page, remember to remove all colon punctuation and spaces. 
* To find the signature we can execute the following commands:

$ echo -n "private key" openssl dgst -sign private.key -sha256 -out sign.sha256

$ openssl enc -base64 -in sign.sha256 -out sign.sha256.sha256

$ cat sign.sha256.sha256

* You will receive a signature value, paste it in WebGoat. You might receive this message on the response "the signature does not match the data",

<figure><img src="../../../../.gitbook/assets/modulus not match data.png" alt=""><figcaption></figcaption></figure>



**Troubleshooting**

* Eiher if you are running on Windows, Mac or Unix, we recommend using WebGoat's Docker container terminal (is a Linux container anyway). 
* You might encounter an error message thatndicates that OpenSSL is unable to read the private key from the `private.key` file, and it suggests there might be an issue with the formatting or the contents of the key file.  Try to follow the format detailed above and separate in three lines the commands related to the private key, in accordance to the details provided by WebGoat.
* We recommend that you use Notepad before pasting values. 

