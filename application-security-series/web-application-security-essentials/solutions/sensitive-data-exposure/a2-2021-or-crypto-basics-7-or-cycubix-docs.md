---
title: "A2:2021 | Crypto Basics (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A2:2021 | Cryptographic Failures | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A2:2021 | Crypto Basics (7) | Cycubix Docs

A keystore is a place where you store keys. Besides _**keystore**_ the term _**truststore**_ is also used frequently. A truststore is the same thing as a keystore. Only it usually contains only the certificates (so basically only public keys and issuer information) of trusted certificates or certificate authorities.

### File based keystores <a href="#file_based_keystores" id="file_based_keystores"></a>

A file based keystore is something that in the end has the keys on a file system. Storing public certificates in a file based keystore is very common.

### Database keystores <a href="#database_keystores" id="database_keystores"></a>

Keys and especially public certificates can of course also be stored in a database.

### Hardware keystore <a href="#hardware_keystore" id="hardware_keystore"></a>

A hardware keystore is a system that has some sort of hardware which contain the actual keys. This is typically done in high end security environments where the private key is really private. In comparison with file based or database keystores, it is impossible to make a copy of the keystore to send it to some unknown and untrusted environment.

Some certificate authorities that are used to provide you with a server certificate for your website, also create the private keys for you (as-a-service). However, it is by definition no longer considered a private key. For all keystore types, you should keep the private key private and use a certificate signing request to order your signing or server certificates.

### Managed keystores in operating system, browser and other applications <a href="#managed_keystores_in_operating_system_browser_and_other_applications" id="managed_keystores_in_operating_system_browser_and_other_applications"></a>

When you visit a website and your browser says that the certificates are fine, it means that the certificate used for the website is issued by a trusted certificate authority. But this list of trusted certificate authorities is managed. Some CA’s might be revoked or removed. These updates happen in the background when browser updates are installed. Not only the browser maintains a list of trusted certificate authorities, the operation system does so as well. And the Java runtime also has its own list which is kept in the cacerts file. Updates of the OS and Java JRE keep this list up to date. In corporate environments, these are usually maintained by the company and also contain company root certificates.

### Extra check for website certificates using DNS CAA records <a href="#extra_check_for_website_certificates_using_dns_caa_records" id="extra_check_for_website_certificates_using_dns_caa_records"></a>

Some companies inspect all or most internet traffic. Even the ones were you think you have an end-2-end secured connection. This works as follows. An employee opens a browser and googles some information. The browser will use https and go to the site of google. The link looks real and the lock is shown in the browser. However, if you would inspect the certificate, you might notice that it has been issued by one of your companies root CA’s! So you have established an end-2-end secure connection with a server of your company, and that server has the secure connection with google. In order to prevent such man in the middle connections to your server, modern browsers now will also check the DNS CAA records to see whether or not a certain issuer is allowed for a certain website. More information: [Wiki DNS CAA](https://en.wikipedia.org/wiki/DNS_Certification_Authority_Authorization)

### Free certificates from Let’s encrypt <a href="#free_certificates_from_lets_encrypt" id="free_certificates_from_lets_encrypt"></a>

[Let’s encrypt](https://letsencrypt.org/) is a free, automated and open Certificate Authority. It allows you to create valid certificates for the websites that you control. By following and implementing a certain protocol, your identity is checked and a certificate will be issued. The certificates are free of charge and this is done to stimulate the use of authorised certificates and to lower the use of self-signed certificates on the internet. Certificates are valid for 90 days, so they need to be automatically renewed. (Which makes sure that the proof of identity/ownership also takes place frequently).
