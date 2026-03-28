---
title: "A7:2021 | Authentication Bypasses (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "A7:2021 | Authentication Bypasses | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7:2021 | Authentication Bypasses (1) | Cycubix Docs

### Authentication Bypasses <a href="#authentication_bypasses" id="authentication_bypasses"></a>

Authentication Bypasses happen in many ways but usually take advantage of some flaw in the configuration or logic. Tampering to achieve the right conditions.

#### Hidden inputs <a href="#hidden_inputs" id="hidden_inputs"></a>

The simplest form is a reliance on a hidden input in the web page/DOM.

#### Removing Parameters <a href="#removing_parameters" id="removing_parameters"></a>

Sometimes, if an attacker doesn’t know the correct value of a parameter, they may remove it from the submission altogether to see what happens.

#### Forced Browsing <a href="#forced_browsing" id="forced_browsing"></a>

If an area of a site is not appropriately protected by configuration, that area of the site may be accessed by guessing/brute-forcing.
