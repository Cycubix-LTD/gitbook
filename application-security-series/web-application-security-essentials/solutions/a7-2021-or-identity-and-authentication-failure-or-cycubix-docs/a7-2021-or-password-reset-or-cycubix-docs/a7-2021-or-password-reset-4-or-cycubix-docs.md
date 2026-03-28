---
title: "A7:2021 | Password Reset (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A7:2021 | Password Reset | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7:2021 | Password Reset (4) | Cycubix Docs

### Security questions <a href="#security_questions" id="security_questions"></a>

This has been an issue and still is for a lot of websites, when you lost your password the website will ask you for a security question which you answered during the sign up process. Most of the time this list contains a fixed number of question and which sometimes even have a limited set of answers. In order to use this functionality a user should be able to select a question by itself and type in the answer as well. This way users will not share the question which makes it more difficult for an attacker.

One important thing to remember the answers to these security question(s) should be treated with the same level of security which is applied for storing a password in a database. If the database leaks an attacker should not be able to perform password reset based on the answer of the security question.

Users share so much information on social media these days it becomes difficult to use security questions for password resets, a good resource for security questions is: [http://goodsecurityquestions.com/](http://goodsecurityquestions.com/)

### Assignment <a href="#assignment" id="assignment"></a>

Users can retrieve their password if they can answer the secret question properly. There is no lock-out mechanism on this 'Forgot Password' page. Your username is 'webgoat' and your favorite color is 'red'. The goal is to retrieve the password of another user. Users you could try are: "tom", "admin" and "larry".

<figure><img src="../../../../../.gitbook/assets/security questions.png" alt=""><figcaption></figcaption></figure>

**Solution**

* We have a hint from the previous lesson. When the user does not exists, the application says "user with this email cannot be found". Which means it does not exisste. Let's start trying with the information given. Usernames like webgoat, larry, admin and tom, with color red. 
* If the user exists we will see the following messages: "Sorry the solution is not correct, please try again". 
* Let's try different colors for user Tom: 

<figure><img src="../../../../../.gitbook/assets/oracle attack.png" alt=""><figcaption></figcaption></figure>

* This is called an oracle attack, which takes advantage of the ability to query the oracle and observe its responses to gain insights that should not be accessible under normal circumstances. There are several types of oracle attacks, including padding oracle attacks, format oracle attacks, and more. 
