---
title: Stand-alone
layout: default
nav_order: 1
parent: "WebGoat Installation | Web Application Security | Cycubix Docs"
grand_parent: "WebGoat | Web Application Security Essentials | Cycubix Docs"
---
# Stand-alone

## **WebGoat 8**

Download the latest WebGoat release from [https://github.com/WebGoat/WebGoat/releases](https://github.com/WebGoat/WebGoat/releases) and start it:

```
java -Dfile.encoding=UTF-8 -jar webgoat-server-8.0.0.VERSION.jar [--server.port=8080] [--server.address=localhost]
```

The latest version of WebGoat needs Java 11. By default WebGoat starts on port 8080 with `--server.port` you can specify a different port. With `server.address` you can bind it to a different address (default localhost).

On AdoptOpenJDK you can download a Java 11 HotSpot, using this link: [https://adoptopenjdk.net/?variant=openjdk11\&jvmVariant=hotspot](https://adoptopenjdk.net/?variant=openjdk11\&jvmVariant=hotspot) you can choose an installer or just a zip package. Make sure that your environment has the location of Java 11.

## **WebWolf**

WebWolf runs as a separate web application and is started automatically when using the Docker image. If you are not using the Docker image you will need to download  the latest WebWolf release from [https://github.com/WebGoat/WebGoat/releases](https://github.com/WebGoat/WebGoat/releases) and start it:

```
java -jar webwolf-<<version>>.jar [--server.port=9090] [--server.address=localhost]
```

By default WebWolf starts on port 9090 with `--server.port` you can specify a different port. With `server.address` you can bind it to a different address (default localhost).
