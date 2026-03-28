---
title: "A1:2021 | Hijack a Session (2) | Cycubix Docs"
layout: default
nav_order: 2
parent: "A1:2021 | Hijack a Session | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Hijack a Session (2) | Cycubix Docs

In this lesson we are trying to predict the 'hijack\_cookie' value. The 'hijack\_cookie' is used to differentiate authenticated and anonymous users of WebGoat.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-06-12 at 18.00.06.png" alt=""><figcaption></figcaption></figure>

## Hints

> ℹ️ **Info**
>
> Check the 'hijack\_cookie' cookie value and think about its format.

> ℹ️ **Info**
>
> The 'hijack\_cookie' is divided in two parts and has the following format '"long number"-"another long number"'.

> ℹ️ **Info**
>
> The 'hijack\_cookie' is divided in two parts and has the following format '"sequential number"-"unix epoch time"'.

> ℹ️ **Info**
>
> Try to send multiple requests to force the creation of new cookies and check if there's any pattern.

> ℹ️ **Info**
>
> Sometimes, authorized users logs into the application.

## **Solution with Burp and ZAP**

**a) Intercepting the session** 

1. Turn on Burp interceptor and click the set on break to start intercepting the HTTP with ZAP. 
2. Go to WebGoat Hijack a Session. 
3. Go to Burp and find the request on HTTP History.  Go to ZAP and see the request on HijackSession/Post:loggin. 

<figure><img src="../../../../../.gitbook/assets/hijack cookie POST.png" alt=""><figcaption></figcaption></figure>

1. Send the POST request to the Repeater (Burp) or the Manual Request Editor (ZAP). 

<figure><img src="../../../../../.gitbook/assets/hijack a session 4.png" alt=""><figcaption></figcaption></figure>

1. Once open in the Repeater / Manual Request Editor, hit "Send" Multiple Times. Server will reply with a Value Set Cookie. 
2. Copy the values of the "Set Cookie".  
3. Close the intercepter or set on the Break. 

<figure><img src="../../../../../.gitbook/assets/hijack a session 4 bis.png" alt=""><figcaption><p><strong>Burp</strong></p></figcaption></figure>

11.  Identify a pattern in the Hijack Cookie number, as you keep on hitting send. 

**Burp**

8538432081538402370-1717442040234

8538432081538402372-1717442064847

8538432081538402373-1717442084267

8538432081538402374-1717442095000

8538432081538402376-1717442105856

8538432081538402377-1717442130639

**Zap**

4687571708252441137-1717631583295

4687571708252441139-1717631609012

We can identify a pattern where the last number of the session ID increase by one, except in some cases where they increase by two. This means that an anonymous user, which suggests that the user had logged in during that period.

Based on hints, it's guessed that the number after "hijack\_cookie" is a timestamp. To get the "hijack\_cookie" of an anonymous user, watch the changing digits of the first part of the "hijack\_cookie" to find the user's first half. The second half is a timestamp that needs brute force within a specific range based on the user's login time difference.

**b) Brute Force Attack**

**ZAP**

* The first half of the "Hijack Cookie" falls between "4687571708252441137" and  "4687571708252441139", meaning "4687571708252441138". For the second half it must fall between "1717631583295 " and "1717631609012". 
* Send POST to Manual Request Editor and Add the hijack\_cookie value=4687571708252441138-1717631583295. 

<figure><img src="../../../../../.gitbook/assets/new hijack cookie.png" alt=""><figcaption><p><strong>Zap</strong></p></figcaption></figure>

* Once you loaded the predicted value of the hijack\_cookie, hit send. 

<figure><img src="../../../../../.gitbook/assets/hijack cookie new results.png" alt=""><figcaption><p><strong>Zap</strong></p></figcaption></figure>

Tips: In this exercise was not necessary, but the Intruder with ZAP is called FUZZ. You can add a payload and range of values for the predicted Hijack\_Cookie, hit the fuzzer and find the predicted value of the hijack\_cookie. 

**Burp**

* The first half of the "Hijack Cookie" falls between "8538432081538402370" and "8538432081538402372", meaning "8538432081538402371". For the second half it must fall between "1717442040234" and "1717442064847". 

1. Send POST request to the intruder. 

<figure><img src="../../../../../.gitbook/assets/hijack send post request to intruder.png" alt=""><figcaption></figcaption></figure>

3. In the intruder, press the button "Clear" on the upper right side of the screen. 

<figure><img src="../../../../../.gitbook/assets/hijack a session intruder.png" alt=""><figcaption></figcaption></figure>

4. Add your hijack\_cookie value. In this case: 8538432081538402371-1717442040234. Select the last digits of the timestamp that will be subject to the brute force attack. 
5. Go to payloads. 

<figure><img src="../../../../../.gitbook/assets/hijack session payloads ok.png" alt=""><figcaption></figcaption></figure>

Select the range of numbers according to the sequence mentioned above: 8538432081538402371-17174420**40234**/17174420**64847.** 

6. Hit the "Attack" Button. 

<figure><img src="../../../../../.gitbook/assets/hijack a session succesfully completd de assignment.png" alt=""><figcaption></figcaption></figure>

## **Troubleshooting**

1. During this exercise it is possible that Proxy service stops, and connection to listener fails. In this case, close the broswer, turn interceptor off. Restart interceptor and Try login in again to Webgoat [http://localhost:8080/WebGoat](http://localhost:8080/WebGoat). 
2. If you receive a "500 Internal Server Error" response in the Repeater, restart your container in Docker.
3.  If the range of numbers selected on the payload do not provide the solution for the completion of the assignment, go back to the post request and identify a new sequence of hijack\_cookies to find a new range of numbers. Don't get frustrated if you need to do this step again...it happens. 



