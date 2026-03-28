---
title: "A10:2021 | Server Side Request Forgery (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A10:2021 | Client Side Request Forgery | Cycubix Docs"
grand_parent: "A10: 2021 | Server Side Request Forgery | Cycubix Docs"
---
# A10:2021 | Server Side Request Forgery (2) | Cycubix Docs

#### Find and modify the request to display Jerry <a href="#find_and_modify_the_request_to_display_jerry" id="find_and_modify_the_request_to_display_jerry"></a>

Click the button and figure out what happened.

<figure><img src="../../../../../.gitbook/assets/STEEL THE CHEESE.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Open ZAP and launch the browser. Go into the corresponding lesson, click on "Steel the Cheese" and intercept the POST request. 

<figure><img src="../../../../../.gitbook/assets/tom cheese 1.png" alt=""><figcaption></figcaption></figure>

* We can see in the url request tom.png. Send the post to the Manual Request Editor and change tom for jerry. 

<figure><img src="../../../../../.gitbook/assets/changed tom for jerry.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/cheese stolen response.png" alt=""><figcaption></figcaption></figure>
