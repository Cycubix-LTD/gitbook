---
title: "A3:2021 | Cross Site Scripting (XSS) (8) | Cycubix Docs"
layout: default
nav_order: 8
parent: "A3:2021 | Cross-Site Scripting (XSS) | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting (XSS) (8) | Cycubix Docs

### Self XSS or reflected XSS? <a href="#self_xss_or_reflected_xss" id="self_xss_or_reflected_xss"></a>

You should have been able to execute the script with the last example. At this point, it is considered 'self XSS,' though.

Why is that?

That is because no link triggers that XSS. You can try it yourself to see what happens …​ go to:

Click on the link given on WebGoat and you will see the following:

[WebGoat/CrossSiteScripting/attack5a?QTY1=1\&QTY2=1\&QTY3=1\&QTY4=1\&field1=\<script>alert('my%20javascript%20here')\</script>4128+3214+0002+1999\&field2=111](https://localhost:8080/WebGoat/CrossSiteScripting/attack5a?QTY1=1\&QTY2=1\&QTY3=1\&QTY4=1\&field1=%3Cscript%3Ealert\(%27my%20javascript%20here%27\)%3C/script%3E4128+3214+0002+1999\&field2=111)

