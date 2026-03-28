---
title: "Challenges | Admin Lost Password | Cycubix Docs"
layout: default
nav_order: 1
parent: "Challenges | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# Challenges | Admin Lost Password | Cycubix Docs

#### Welcome to the WebGoat challenge (CTF) <a href="#welcome_to_the_webgoat_challenge_ctf" id="welcome_to_the_webgoat_challenge_ctf"></a>

**Introduction**

The challenges contain more a CTF like lessons where we do not provide any explanations what you need to do, no hints will be provided. You can use these challenges in a CTF style where you can run WebGoat on one server and all participants can join and hack the challenges. A scoreboard is available at [scoreboard](http://localhost:8080/WebGoat/scoreboard)

In this CTF you will need to solve a couple of challenges, each challenge will give you a flag which you will\
need to post in order to gain points.

Flags have the following format: `a7179f89-906b-4fec-9d99-f15b796e7208`

**Rules**

* Do not try to hack the competition infrastructure. If you happen to find a bug or vulnerability please send us\
  an e-mail.
* Play fair, do not try sabotage other competing teams, or in any way hindering the progress of another team.
* Brute forcing of challenges / flags is not allowed.

**Have fun!!**\
Team WebGoat

<figure><img src="../../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/admin lost.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Open ZAP or BurpSuite and intercept the request. 

<figure><img src="../../../../.gitbook/assets/logo.png" alt=""><figcaption></figcaption></figure>

* Send the request to the Manual Request Editor (ZAP) or the Repeater (BURP). 
* Press send: 

<figure><img src="../../../../.gitbook/assets/LOGO ANSWER.png" alt=""><figcaption></figcaption></figure>

* Change the response from image to text: 

<br>

<figure><img src="../../../../.gitbook/assets/admin1366.png" alt=""><figcaption></figcaption></figure>

* Submit into WebGoat the corresponding information for username and password: 

<figure><img src="../../../../.gitbook/assets/ctf admin.png" alt=""><figcaption></figcaption></figure>
