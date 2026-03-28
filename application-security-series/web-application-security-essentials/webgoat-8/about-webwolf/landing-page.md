---
description: You can use WebWolf as your landing page for harvesting cookies when you perform an XSS lesson. Learn more about Webwolf landing page for incoming requests
title: "WebWolf Landing Page | Web Application Security | Cycubix Docs"
layout: default
nav_order: 3
parent: "WebWolf | Web Application Security | Cycubix Docs"
grand_parent: "WebGoat | Web Application Security Essentials | Cycubix Docs"
---
# WebWolf Landing Page | Web Application Security | Cycubix Docs

## Landing page <a href="#landing_page" id="landing_page"></a>

This page will show all the requests made to '/landing/\*\*'. This means you can use WebWolf as your landing page for harvesting cookies etc which is helpful when you perform a XSS lesson.

![](<../../../../.gitbook/assets/image (22).png>)

**For this exercise, you need to log in to WebWolf first.**

Please note that after resetting the password, the user will encounter an error page. In an actual attack scenario, the user would likely see a standard success page (this limitation is due to WebWolf's constraints).

If we successfully deceive a user into clicking a link in an email, this link will direct them to our crafted password reset page. This page appears identical to the company's legitimate password reset page. When the user enters a new password and submits it, the password is sent to your host. In this scenario, the password is sent to WebWolf.

Search for the unique code and solve this exercise. 

**For this exercise you need to login to WebWolf first.**

Suppose we tricked a user to click on a link he/she received in an email, this link will open up our crafted password reset link page. The user does not notice any differences compared to the normal password reset page of the company. The user enters a new password and hits enter. 

The new password will be sent to your host. In this case the new password will be sent to WebWolf. Try to locate the unique code.

Please be aware that after resetting the password the user will receive an error page. In a real attack scenario the user would probably see a normal success page (this is due to a limit what we can control with WebWolf). 
