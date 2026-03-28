---
title: "A5:2021 | Security Misconfiguration (12) | Cycubix Docs"
layout: default
nav_order: 12
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (12) | Cycubix Docs

### XXE mitigation <a href="#xxe_mitigation" id="xxe_mitigation"></a>

In order to protect against XXE attacks you need to make sure you validate the input received from an untrusted client. In the Java world you can also instruct your parser to ignore DTD completely, for example:

```
XMLInputFactory xif = XMLInputFactory.newFactory();
xif.setProperty(XMLInputFactory.SUPPORT_DTD, false);
```

if you are not able to completely switch off the DTD support, you can also instruct the XML parser to ignore external entities, like:

```
XMLInputFactory xif = XMLInputFactory.newFactory();
xif.setProperty(XMLInputFactory.IS_SUPPORTING_EXTERNAL_ENTITIES, false);
xif.setProperty(XMLInputFactory.SUPPORT_DTD, true);
```

For more information about configuration, see [XXE prevention sheet](https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html)

#### Validate <a href="#validate" id="validate"></a>

Implement proper validation for the Content-type and Accept header do not simply rely on the framework to handle the incoming request. If the client specifies a proper accept header return with a \`406/Not Acceptable.
