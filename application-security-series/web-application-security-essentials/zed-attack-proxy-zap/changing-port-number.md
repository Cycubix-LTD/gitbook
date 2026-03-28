---
description: You can change the ZAP port number by opening ZAP tools, going to options, and selecting local proxy. Learn how to change the default ZAP port with our quick ZAP guide.
title: "ZAP | ZAP Proxy | Cycubix Docs"
layout: default
nav_order: 3
parent: "ZAP | Web Application Security Essentials | Cycubix Docs"
grand_parent: Web Application Security Essentials
---
# ZAP | ZAP Proxy | Cycubix Docs

Change ZAP Port by opening ZAP, Tools–> Options –> local proxy. Change the default 8080 port to 8084 and you should be good to run both WebGoat (on 8080) and ZAP on 8090.

![](<../../../.gitbook/assets/image (2).png>)

## **Troubleshooting**

### **Port Conflict**

When installing ZAP check for port conflicts.  ZAP typically uses port 8080 by default. If another application is using this port, you might encounter issues. Check if any other applications (like WebGoat) are using the same port.

You can use the following commands to check port usage: 

* Windows: netstat -ano | findstr :8080.
* MacOS: sudo lsof -i :8080 .

If another application is using port 8080, you can change the default port ZAP uses by editing the configuration file or specifying a different port when starting ZAP. Follow the instructions mentioned above for changing the port. 

### File locks and permissions

* Ensure that the file or directory ZAP is trying to access is not locked by another application and that you have the necessary permissions to access it.
* Check if any antivirus or security software is blocking ZAP from accessing required files. 
