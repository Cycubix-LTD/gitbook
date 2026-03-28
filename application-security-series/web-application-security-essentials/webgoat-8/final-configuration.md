---
description: Besides using the default URL you can also create fully qualified domain names (FQDN) for WebGoat and WebWolf. Read our guide & learn how to configurate WebGoat.
title: "WebGoat Configuration | Web Application Security | Cycubix Docs"
layout: default
nav_order: 3
parent: "WebGoat | Web Application Security Essentials | Cycubix Docs"
grand_parent: Web Application Security Essentials
---
# WebGoat Configuration | Web Application Security | Cycubix Docs

## Fully Qualified Domain Names (FQDN)

Besides using the default URL’s you can also create fully qualified domain names (FQDN) for WebGoat and WebWolf. You will need to edit the hosts file for Windows / Mac.

```
#Windows, edit the following file with the below contents
c:\system32\drivers\etc\hosts

#On MacOS, edit the following file with
/etc/hosts

127.0.0.1 www.webgoat.local www.webwolf.local
```

## **Troubleshooting**

* If you can't find the path to c:\system32\drivers\etc\hosts, open your Notepad App as an administrator and put the following path into the file address: c:\system32\drivers\etc\hosts. Then make the corresponding FQDN changes. 
* Download and run WebGoat with the necessary configuration to bind to the specified FQDN.

        java -jar webgoat-server-8.0.0.M26.jar --server.address=webgoat.local

* Open a web browser and navigate to `http://webgoat.local:8080/WebGoat`. You should see the WebGoat login screen, indicating that the configuration was successful.

