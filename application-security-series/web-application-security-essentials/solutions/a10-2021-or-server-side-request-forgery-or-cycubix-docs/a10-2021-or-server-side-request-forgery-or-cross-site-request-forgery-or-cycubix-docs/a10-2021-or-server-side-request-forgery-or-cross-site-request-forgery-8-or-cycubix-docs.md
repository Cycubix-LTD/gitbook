---
title: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (8) | Cycubix Docs"
layout: default
nav_order: 8
parent: "A10:2021 | Server Side Request Forgery | Cross Site Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery | Cross Site Request Forgery (8) | Cycubix Docs

### Login CSRF attack <a href="#login_csrf_attack" id="login_csrf_attack"></a>

In a login CSRF attack, the attacker forges a login request to an honest site using the attacker’s username and password at that site. If the forgery succeeds, the honest server responds with a `Set-Cookie` header that instructs the browser to mutate its state by storing a session cookie, logging the user into the honest site as the attacker. This session cookie is used to bind subsequent requests to the user’s session and hence to the attacker’s authentication credentials. 

Login CSRF attacks can have serious consequences, for example see the picture below where an attacker created an account at google.com the victim visits the malicious website and the user is logged in as the attacker. The attacker could then later on gather information about the activities of the user.

<figure><img src="../../../../../.gitbook/assets/scrf robust defenses.png" alt=""><figcaption></figcaption></figure>

For more information read the following [paper](http://seclab.stanford.edu/websec/csrf/csrf.pdf).

In this assignment try to see if WebGoat is also vulnerable for a login CSRF attack. Leave this tab open and in another tab create a user based on your own username prefixed with `csrf-`. So if your username is `tom` you must create a new user called `csrf-tom`.

Login as the new user. This is what an attacker would do using CSRF. Then click the button in the original tab. Because you are logged in as a different user, the attacker learns that you clicked the button.

<figure><img src="../../../../../.gitbook/assets/crsf lesson.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Hint: First create a new account with csrf-username. Create a form which will log you in as this user (hint 1) and upload it to WebWolf. Visit this assignment again. 
* Let's go ahead and create a new user. 
* Then create an HTML with the following code: 

````
```html
<form action="http://localhost:8080/WebGoat/login" method="POST" style="width 300 px;">
<input type="hidden" name="username" value="csfr-user">
<input type="hidden" name="password" value="password">
<button type="submit">Sign in</button>
</form>
<script>document.login.submit()</script>
```
````

* Log in as your original user. Then open in the browser of your choice your saved HTML file. 

<figure><img src="../../../../../.gitbook/assets/sign in.png" alt=""><figcaption></figcaption></figure>

* Then go back again into your previous log in WebGoat page. You will be now signed in into 2 different accounts. 

<figure><img src="../../../../../.gitbook/assets/log in user 1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/scrf luz clarita (1).png" alt=""><figcaption></figcaption></figure>

* From your original account click solved on the exercise. Then you will see that your are now  now logged in as the csrf-\<your\_username> user. 
