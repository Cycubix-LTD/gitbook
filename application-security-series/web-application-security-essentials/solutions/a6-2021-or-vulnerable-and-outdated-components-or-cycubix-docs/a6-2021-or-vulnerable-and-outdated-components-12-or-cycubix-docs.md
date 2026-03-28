---
title: "A6:2021 | Vulnerable and Outdated Components (12) | Cycubix Docs"
layout: default
nav_order: 12
parent: "A6:2021 | Vulnerable and Outdated Components | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A6:2021 | Vulnerable and Outdated Components (12) | Cycubix Docs

### Exploiting [CVE-2013-7285](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-7285) (XStream) <a href="#exploiting_cve_2013_7285_xstream" id="exploiting_cve_2013_7285_xstream"></a>

This lesson only works when you are using the Docker image of WebGoat. 

WebGoat uses an XML document to add contacts to a contacts database.

```
<contact>
    <id>1</id>
    <firstName>Bruce</firstName>
    <lastName>Mayhew</lastName>
    <email>webgoat@owasp.org</email>
</contact>
```

The java interface that you need for the exercise is: [org.owasp.webgoat.lessons.vulnerablecomponents](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/).

Contact:  Start by sending the above contact to see what the normal response would be and then read the CVE vulnerability documentation (search the Internet) and try to trigger the vulnerability.

 For this example, we will let you enter the XML directly versus intercepting the request and modifying the data. You provide the XML representation of a contact and WebGoat will convert it a Contact object using `XStream.fromXML(xml)`.

<figure><img src="../../../../.gitbook/assets/xml doc.png" alt=""><figcaption></figcaption></figure>

Solution: 

* Hints: Did you search for CVE-2013-728 and read https://x-stream.github.io/CVE-2013-7285.html?. Did you read the blogpost of Dinis Cruz provided in the previous page?.  We recommend this reading also for you to solve this lab: [**pwntester.**](https://www.pwntester.com/blog/2013/12/23/rce-via-xstream-object-deserialization38/) 
* CVE-2013-7285 is a critical security vulnerability affecting XStream, a popular Java library used for converting objects to XML and vice versa. When XStream processes an XML stream to recreate Java objects, it relies on type information embedded in the XML. An attacker can exploit this mechanism by injecting a payload that includes a harmful class such as `java.lang.ProcessBuilder`, which can be used to execute commands.
* From Dinis Cruz blogpost we can extract a he proof of concept that typically involves deserializing a malicious payload that can exploit the vulnerability. In the context of XStream, this means crafting an XML input that results in unintended code execution.
* As mentioned in the exercise, the root element is "contact" and we need to link it to a proxy object. We need to also define the dynamic proxy elements. We will need to add the event listeners. 
* Within the "Handler" element we will need to define the target class that will handle the evebts and by specifying the class, the payload will aim to execute a system command. 
* We need to define the command and the action. 

```
<contact class='dynamic-proxy'> <interface>org.owasp.webgoat.lessons.vulnerablecomponents.Contact</interface>
  <handler class='java.beans.EventHandler'>
    <target class='java.lang.ProcessBuilder'>
      <command>
        <string>calc.exe</string>
      </command>
    </target>
    <action>start</action>
  </handler>
</contact>
```

<figure><img src="../../../../.gitbook/assets/xml representation.png" alt=""><figcaption></figcaption></figure>
