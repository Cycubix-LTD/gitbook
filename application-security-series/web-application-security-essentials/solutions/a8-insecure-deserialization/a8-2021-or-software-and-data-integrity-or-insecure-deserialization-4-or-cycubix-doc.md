---
title: "A8:2021 | Software and Data Integrity | Insecure Deserialization (4) | Cycubix Doc"
layout: default
nav_order: 4
parent: "A8:2021 | Software and Data Integrity | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A8:2021 | Software and Data Integrity | Insecure Deserialization (4) | Cycubix Doc

### What is a Gadgets Chain <a href="#what_is_a_gadgets_chain" id="what_is_a_gadgets_chain"></a>

It is weird (but it could happen) to find a gadget that runs dangerous actions itself when is deserialized. However, it is much easier to find a gadget that runs action on other gadget when it is deserialized, and that second gadget runs more actions on a third gadget, and so on until a real dangerous action is triggered. That set of gadgets that can be used in a deserialization process to achieve dangerous actions is called "Gadget Chain".

Finding gadgets to build gadget chains is an active topic for security researchers. This kind of research usually requires to spend a big amount of time reading code.



