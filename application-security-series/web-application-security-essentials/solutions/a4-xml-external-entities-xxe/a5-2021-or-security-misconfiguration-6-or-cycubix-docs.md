---
title: "A5:2021 | Security Misconfiguration (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (6) | Cycubix Docs

#### Find XXE with a code review <a href="#find_xxe_with_a_code_review" id="find_xxe_with_a_code_review"></a>

Now we know how the injection work, let’s look at why this can happen. In Java applications XML library configuration is not secure by default, and you have to change the settings. Suppose you find the following code snippet during a code review:

```
public XmlMapper xmlMapper() {
  return new XmlMapper(XMLInputFactory.newInstance()) 
}
```

while having a look at the release notes of the Jackson library you read:

> 211: Disable `SUPPORT_DTD` for `XMLInputFactory` unless explicitly overridden

— Jackson 2.7.8 (26-Sep-2016)

**Question: is the parser vulnerable?**

This piece of code defines a new `XmlMapper` (`ObjectMapper`) which is a popular framework for reading and writing xml and json. If we follow the code one level deeper we find:

```
/**
 * @since 2.4
 */
public XmlMapper(XMLInputFactory inputF) {   
  this(new XmlFactory(inputF));  
}
```

This is the 'constructor' we called from the listing above (1)

Call to another 'constructor' and initialize a new instance of `XmlFactory`

Let’s take a look at the source code of `XMLFactory`

```
public XmlFactory(XMLInputFactory xmlIn) {  
  this(xmlIn, null); }  

protected XmlFactory(XMLInputFactory xmlIn, XMLOutputFactory xmlOut, ...) { 
  if (xmlIn == null) {  
    xmlIn = XMLInputFactory.newInstance();
    // as per [dataformat-xml#190], disable external entity expansion by default
    xmlIn.setProperty(XMLInputFactory.IS_SUPPORTING_EXTERNAL_ENTITIES, Boolean.FALSE);  
    // and ditto wrt [dataformat-xml#211], SUPPORT_DTD
    xmlIn.setProperty(XMLInputFactory.SUPPORT_DTD, Boolean.FALSE); 
  }
}
```

This is the 'constructor' definition of the new instance created in 3

Call to another 'constructor' defined in 3

In 4 we know `if (xmlIn == null)` will not be true because if we look at our declaration at the top we created our own instance `XMLInputFactory.newInstance()` which is not `null`. This means that we have a XML parser which is by default **not** secured against XXE injection. The interesting part at 5 and 6 is the extra protection nested inside the if statement.

If we look at the Spring Boot framework for example how they initialize the same parser:

```
public ObjectMapper create() {
  return new XmlMapper(xmlInputFactory());  
}

private static XMLInputFactory xmlInputFactory() {
  XMLInputFactory inputFactory = XMLInputFactory.newInstance();
  inputFactory.setProperty(XMLInputFactory.SUPPORT_DTD, false);
  inputFactory.setProperty(XMLInputFactory.IS_SUPPORTING_EXTERNAL_ENTITIES, false);
  return inputFactory;
}
```

```
Call to a method which initializes the parser safely
```

As you can see the explicitly define the `XMLInputFactory` through the private method `xmlInputFactory()` which actually sets the same properties to the parser as we saw in the previous listing.

As you can see this it is not that easy to find out whether the parser is secure against the injection you really have to dig deep in the code, and the library to find out what the parser settings are.

Take a look at [XXE prevention sheet](https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html) for more ways to secure your parser.
