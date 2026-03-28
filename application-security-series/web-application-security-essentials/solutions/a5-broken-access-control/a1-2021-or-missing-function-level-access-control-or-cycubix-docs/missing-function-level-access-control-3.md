---
title: "A1:2021 | Missing Function Level Access Control (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A1:2021 | Missing Function Level Access Control | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Missing Function Level Access Control (3) | Cycubix Docs

### Just Try It <a href="#just_try_it" id="just_try_it"></a>

As the previous page noted, sometimes apps rely on client controls. to control access (obscurity). If you can find items that don’t have visible links, just try them, see what happens. Yes, it can be that simple!

#### Gathering User Info <a href="#gathering_user_info" id="gathering_user_info"></a>

Often times, data dumps from vulnerabilities such as sql injection, but they can also come from poor or lacking access control.

It will likely take multiple steps and multiple attempts to get this one. Pay attention to the comments, leaked info. and you’ll need to guess some. You may need to use another browser/account along the way. Start with the info. you already gathered (hidden menu items) to see if you can pull the list of users and then provide the 'Hash' for your own user account.

![](<../../../../../.gitbook/assets/Screenshot 2020-04-28 at 16.43.55.png>)

**Solution with ZAP and BurpSuite**

* From previous lessons we know that there are 2 endpoints that are supposed to be hidden from a non-admin user: /users and /config. 
* Turn on the interceptor on Burp/ Unset the Break on Zap. 
* Go Back to WebGoat and hit the Submit button under hash. 
* On Burp and ZAP find the request with the endpoint we are looking for: 

<figure><img src="../../../../../.gitbook/assets/missing function access control user hash to users.png" alt=""><figcaption></figcaption></figure>

* Turn Off the Interceptor (Burp) or Break (ZAP). 
* Send the request to the Repeater (Burp) or Manual Request Editor (ZAP). Change the endpoint from user-hash to users. 
* Click send. You will receive and error message, saying the media type is unsupported. 
*   Change content type: 

    ```
    Content-Type: application/json; charset=UTF-8
    ```
* After hitting send, you will receive a message of error saying that it was expected a JSON object in accordance with the POST request. 
* Change the Method from POST to GET. And add a value into userHash. 

<figure><img src="../../../../../.gitbook/assets/missing function level access control get .png" alt=""><figcaption></figcaption></figure>

* After hitting send, you will get the following values: 

<figure><img src="../../../../../.gitbook/assets/missing function level has users correct.png" alt=""><figcaption></figcaption></figure>

* Submit the UserHash in the WebGoat lesson. Don't forget to previously turn on the Interceptor or Breaker. 

#### HINTS  FOR THE  HARDER WAY OF SOLVING THE LAB WITH DEVELOPER TOOLS

* Now for the harder way ... it builds on the easier way'
* If the request to view users, were a 'service' or 'RESTful' endpoint, what would be different about it?
*  If you're still looking for hints ... try changing the Content-type header as in the GET request.
* You also need to deliver a proper payload for the request (look at how registration works). This should be formatted in line with the content-type you just defined.
* You will want to add WEBGOAT\_ADMIN for the user's role. Yes, you'd have to guess/fuzz this in a real-world setting.
* OK, here it is. First, create an admin user ... Change the method to POST, change the content-type to "application/json". And your payload should look something like: {"username":"newUser2","password":"newUser12","matchingPassword":"newUser12","role":"WEBGOAT\_ADMIN"}.
* Now log in as that user and bring up WebGoat/users. Copy your hash and log back in to your original account and input it there to get credit.
* Open the _Development Tools_ in the browser, and go to the _Network_ tab.
* Go to [http://host:port/WebGoat/users](http://host/:port/WebGoat/users).
* Locate the query to `users` in the _Network_ tab and click on _Edit and Resend_.
* Add the header `Content-Type: application/json`.
* Check the hash in the response.
