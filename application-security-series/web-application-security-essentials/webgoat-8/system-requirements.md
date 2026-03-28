---
description: In order to utilize WebGoat and WebWolf you need to fulfil the system requirements. Set up your pc and fulfil system requirements for mac & windows now.
title: "WebGoat & WebWolf System Requirements | Cycubix Docs"
layout: default
nav_order: 5
parent: "WebGoat | Web Application Security Essentials | Cycubix Docs"
grand_parent: Web Application Security Essentials
---
# WebGoat & WebWolf System Requirements | Cycubix Docs

In order to utilize [WebGoat ](https://owasp.org/www-project-webgoat/)and [WebWolf](about-webwolf/), you need to fulfil the system requirements and set up your laptop / PC as described below.

#### Mac Users

* Mac hardware must be a 2010 or newer model, with Intel’s hardware support for memory management unit (MMU) virtualization, including Extended Page Tables (EPT) and Unrestricted Mode. You can check to see if your machine has this support by running the following command in a terminal: sysctl kern.hv\_support.
* MacOS El Capitan 10.11 and newer macOS releases are supported. We recommend upgrading to the latest version of macOS.
* At least 4GB of RAM (recommended 8GB).
* VirtualBox prior to version 4.3.30 must NOT be installed (it is incompatible with Docker for Mac). If you have a newer version of VirtualBox installed, it’s fine.
* More details: [https://docs.docker.com/docker-for-mac/](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

#### Windows Users

* Windows 10 Professional, Enterprise or Education editions.
* At least 4GB of RAM (recommended 8GB).
* Docker for Windows requires Microsoft Hyper-V to run. The Docker for Windows installer enables Hyper-V for you, if needed, and restart your machine. After Hyper-V is enabled, VirtualBox no longer works, but any VirtualBox VM images remain.
* More details: [https://docs.docker.com/docker-for-windows/](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
