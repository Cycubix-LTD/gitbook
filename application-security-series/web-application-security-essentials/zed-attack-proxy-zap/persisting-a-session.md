---
description: When you first start ZAP, you will be asked if you want to persist the ZAP session. Learn the difference between not persisting and persisting the ZAP session.
title: "ZAP | Persist ZAP Session | Cycubix Docs"
layout: default
nav_order: 2
parent: "ZAP | Web Application Security Essentials | Cycubix Docs"
grand_parent: Web Application Security Essentials
---
# ZAP | Persist ZAP Session | Cycubix Docs

## **Persist or Not to Persist Zap session**

When you first start ZAP, you will be asked if you want to persist the ZAP session. By default, ZAP sessions are always recorded to disk in a HSQLDB database with a default name and location. If you do not persist the session, those files are deleted when you exit ZAP.

If you choose to persist a session, the session information will be saved in the local database so you can access it later, and you will be able to provide custom names and locations for saving the files.

 <img src="https://www.zaproxy.org/getting-started/images/zap-persist-session.png" alt="" data-size="original">

For now, select **No, I do not want to persist this session at this moment in time**, then click **Start**. The ZAP sessions will not be persisted for now.
