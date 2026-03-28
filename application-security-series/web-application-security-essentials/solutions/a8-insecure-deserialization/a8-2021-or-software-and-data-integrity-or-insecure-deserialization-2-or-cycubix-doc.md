---
title: "A8:2021 | Software and Data Integrity  | Insecure Deserialization (2) | Cycubix Doc"
layout: default
nav_order: 2
parent: "A8:2021 | Software and Data Integrity | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A8:2021 | Software and Data Integrity  | Insecure Deserialization (2) | Cycubix Doc

### What is Serialization <a href="#what_is_serialization" id="what_is_serialization"></a>

Serialization is the process of turning some object into a data format that can be restored later. People often serialize objects in order to save them to storage, or to send as part of communications. Deserialization is the reverse of that process taking data structured from some format, and rebuilding it into an object. Today, the most popular data format for serializing data is JSON. Before that, it was XML.

```
a:4:{i:0;i:132;i:1;s:7:"Mallory";i:2;s:4:"user"; i:3;s:32:"b6a8b3bea87fe0e05022f8f3c88bc960";}
```

#### Native Serialization <a href="#native_serialization" id="native_serialization"></a>

Many programming languages offer a native capability for serializing objects. These native formats usually offer more features than JSON or XML, including customizability of the serialization process. Unfortunately, the features of these native deserialization mechanisms can be repurposed for malicious effect when operating on untrusted data. Attacks against deserializers have been found to allow denial-of-service, access control, and remote code execution attacks.

#### Known Affected Programming Languages <a href="#known_affected_programming_languages" id="known_affected_programming_languages"></a>

* PHP
* Python
* Ruby
* Java
* C
* C++

#### Data, not Code <a href="#data_not_code" id="data_not_code"></a>

ONLY data is serialized. Code is not serialized itself. Deserialization creates a new object and copies all the data from the byte stream, in order to obtain and object identical to the object that was serialized.
