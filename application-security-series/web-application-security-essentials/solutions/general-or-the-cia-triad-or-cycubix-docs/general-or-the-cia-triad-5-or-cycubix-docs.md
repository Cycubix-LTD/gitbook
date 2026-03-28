---
title: "General | The CIA Triad (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "General | The CIA Triad | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | The CIA Triad (5) | Cycubix Docs

## Quiz

Now it’s time for a quiz! Answer the following question to check if you understood the topic.

Today, most systems are protected by a firewall. A properly configured firewall can prevent malicious entities from accessing a system and helps protect an organization’s resources. For this quiz, imagine a system that handles personal data but is not protected by a firewall:

1\. How could an intruder harm the security goal of confidentiality?

Solution 1: By deleting all the databases.\
Solution 2: By stealing a database where general configuration information for the system is stored.\
<mark style="color:green;">Solution 3: By stealing a database where names and emails are stored and uploading it to a website.</mark>\
Solution 4: Confidentiality can't be harmed by an intruder.<br>

2\. How could an intruder harm the security goal of integrity?

<mark style="color:green;">Solution 1: By changing the names and emails of one or more users stored in a database.</mark>\
Solution 2: By listening to incoming and outgoing network traffic.\
Solution 3: By bypassing authentication mechanisms that are in place to manage database access.\
Solution 4: Integrity can only be harmed when the intruder has physical access to the database storage.<br>

3\. How could an intruder harm the security goal of availability?

Solution 1: By exploiting bugs in the systems software to bypass authentication mechanisms for databases.\
Solution 2: By redirecting emails with sensitive data to other individuals.\
Solution 3: Availability can only be harmed by unplugging the power supply of the storage devices.\
<mark style="color:green;">Solution 4: By launching a denial of service attack on the servers.</mark><br>

4\. What happens if at least one of the CIA security goals is harmed?

Solution 1: A system can be considered safe until all the goals are harmed. Harming one goal has no effect on the systems security.\
<mark style="color:green;">Solution 2: The systems security is compromised even if only one goal is harmed.</mark>\
Solution 3: It's not that bad when an attacker reads or changes data, at least some data is still available, hence only when the goal of availability is harmed the security of the system is compromised.\
Solution 4: It shouldn't be a problem if an attacker changes data or makes it unavailable, but reading sensitive data is not tolerable. Theres only a problem when confidentiality is harmed.

<figure><img src="../../../../.gitbook/assets/cia triad 5.png" alt=""><figcaption></figcaption></figure>
