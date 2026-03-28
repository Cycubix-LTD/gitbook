---
title: "A1:2021 | Missing Function Level Access Control (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "A1:2021 | Missing Function Level Access Control | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Missing Function Level Access Control (1) | Cycubix Docs

**Missing Function Level Access Control**

Access control, like preventing XSS with output encoding, can be tricky to maintain. One must ensure it is adequately enforced throughout the entire application, thus in every method/function.

#### IDOR vs Missing Function Level Access Control <a href="#idor_vs_missing_function_level_access_control" id="idor_vs_missing_function_level_access_control"></a>

The fact is many people (including the author of this lesson) would combine function level access control and IDOR into 'Access Control.' 

For the sake of OWASP Top 10 and these lessons, we will make a distinction. The distinction most made is that IDOR is more of a 'horizontal' or 'lateral' access control issue, and missing function level access control 'exposes functionality.' Even though the IDOR lesson here demonstrates how functionality may also be exposed (at least to another user in the same role), we will look at other ways functionality might be exposed.

