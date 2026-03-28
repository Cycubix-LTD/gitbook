---
title: "General | HTTP Proxies (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "General | HTTP Proxies | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# General | HTTP Proxies (7) | Cycubix Docs

## Proxy from ZAP to HTTPS <a href="#proxy_from_zap_to_https" id="proxy_from_zap_to_https"></a>

The ZAP proxy can also be configured to proxy **HTTPS** requests. It will terminate the HTTPS connection in ZAP and then proxy it to the target using its keystore. You can even proxy to sites with mutual TLS. In that case, you configure ZAP with the keystore and key to use for the connection.

In ZAP Go to **Tools/Options/Client Certificate** to proxy to a mutual TLS HTTPS site. 

Go to **Tools/Options/Connection** if you want to set timeouts and want to force the use of TLSv1.2 e.g.

#### Export the certificate <a href="#export_the_certificate" id="export_the_certificate"></a>

Depending on the local tools installation, ZAP can start a browser directly with some adjusted options like network settings and certificate adjustments. 

However, you should do this step if you want to start your browser independently of ZAP. To be able to use the browser, the browser needs the certificate, which you can export here:

<figure><img src="../../../../.gitbook/assets/http proxies 7  (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/http proxies 7 bis (1).png" alt=""><figcaption></figcaption></figure>

#### Import the OWASP ZAP root certificate <a href="#import_the_owasp_zap_root_certificate" id="import_the_owasp_zap_root_certificate"></a>

1. Go to your Firefox Preferences (Mac, Linux) or Options (Windows) from the menu.\`
2. Search for _certificates._
3. Click _View certificates._
4. Import the ZAP root certificate that was saved (see the previous page).

<figure><img src="../../../../.gitbook/assets/HTTP proxies 7 bis x2.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/HTTP proxies 7 bis x3 (1).png" alt=""><figcaption></figcaption></figure>

**Troubleshooting**

If the connection is not working in Chrome after applying proxy settings, here are some steps to troubleshoot the issue:

1. **Verify Proxy Settings:**
   * Ensure that the proxy IP is set to `127.0.0.1` and the port to `8090`.
2. **Check ZAP is Running:**
   * Ensure ZAP is running and listening on port 8090.
3. **Check Network Connection:**
   * Verify your internet connection is working without the proxy.
4. **Firewall/Antivirus:**
   * Ensure your firewall or antivirus is not blocking the connection.
5. **Reset Proxy Settings:**
   * Temporarily reset proxy settings in Chrome to check if the issue is specific to the proxy configuration.
