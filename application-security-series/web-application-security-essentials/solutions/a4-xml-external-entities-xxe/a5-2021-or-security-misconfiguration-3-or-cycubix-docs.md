---
title: "A5:2021 | Security Misconfiguration (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (3) | Cycubix Docs

#### XXE example <a href="#xxe_example" id="xxe_example"></a>

Let’s look at an example of an XXE injection, in the previous section we saw that XML entities can be used as follows:

```
<?xml version="1.0" standalone="yes" ?>
<!DOCTYPE author [
  <!ELEMENT author (#PCDATA)>
  <!ENTITY js "Jo Smith">
]>
<author>&js;</author>
```

#### External DTD declaration <a href="#external_dtd_declaration" id="external_dtd_declaration"></a>

Defining these entities also makes it possible to define another DTD in an external file, for example:

```
<?xml version="1.0"?>
<!DOCTYPE note SYSTEM "email.dtd">
<email>
  <to>webgoat@webgoat.org</to>
  <from>webwolf@webwolf.org</from>
  <subject>Your app is great, but contains flaws</subject>
  <body>Hi, your application contains some SQL injections</body>
</email>
```

and the `email.dtd` can be defined as follows:

```
<!ELEMENT email (to,from,title,body)>
<!ELEMENT to (#PCDATA)>
<!ELEMENT from (#PCDATA)>
<!ELEMENT subject (#PCDATA)>
<!ELEMENT body (#PCDATA)>
```

#### XXE <a href="#xxe" id="xxe"></a>

If a XML parser is configured to allow external DTD or entities we can change the following XML snippet with the following:

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE author [
  <!ENTITY js SYSTEM "file:///etc/passwd">
]>
<author>&js;</author>
```

Now what happens? We defined an include from the local filesystem, the XML parser will load the file and will add the contents wherever the entity is referenced. Let’s assume the XML message is returned to the user the message will be:

<figure><img src="../../../../.gitbook/assets/XXE IMAGE 1.png" alt=""><figcaption></figcaption></figure>

The extra document type definition(DOCTYPE) is something you can always add to the xml document and if the parser settings are enabled to allow external entities to be processed you are off to a good start for finding a XXE injection.
