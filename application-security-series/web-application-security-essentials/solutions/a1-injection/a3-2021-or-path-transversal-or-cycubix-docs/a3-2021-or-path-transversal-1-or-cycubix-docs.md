---
title: "A3: 2021 | Path Transversal (1) | Cycubix Docs"
layout: default
nav_order: 1
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3: 2021 | Path Transversal (1) | Cycubix Docs

#### Path traversal <a href="#path_traversal" id="path_traversal"></a>

A path(directory) traversal is a vulnerability where an attacker can access or store files and directories outside the application’s location. It may lead to reading files from other directories and overwriting critical system files in case of a file upload.

#### How does it work? <a href="#how_does_it_work" id="how_does_it_work"></a>

For example, let’s assume we have an application that hosts some files, in the following format: [`http://example.com/file=report.pdf`](http://example.com/file=report.pdf) now as an attacker, you are interested in other files, of course, so you try [`http://example.com/file=../../../../../etc/passwd`](http://example.com/etc/passwd)`.` In this case, you try walking up to the root of the filesystem and then go into `/etc/passwd` to gain access to this file. The `../` is called **dot-dot-slash**, another name for this attack.

Of course, this is a straightforward example, and in most cases, this will not work as frameworks implemented controls.

So we need to get a little more creative and start encoding `../` before the request is sent to the server. For example, if we URL encode `../`, you will get `%2e%2e%2f`, and the webserver receiving this request will decode it again to `../`.

Also, note that avoiding applications filtering those encodings double encoding might work as well. Double encoding might be necessary when you have a system A which calls system B. System A will only decode once and call B with the still encoded URL.
