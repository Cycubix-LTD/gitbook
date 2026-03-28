---
title: "A6:2021 | Vulnerable and Outdated Components (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A6:2021 | Vulnerable and Outdated Components | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A6:2021 | Vulnerable and Outdated Components (7) | Cycubix Docs

### How do I generate a Bill of Materials <a href="#how_do_i_generate_a_bill_of_materials" id="how_do_i_generate_a_bill_of_materials"></a>

There are several open source and paid-for solutions that will identify risk in components. However, there are not many tools that will deliver a complete list of "ingredients" used within an application. OWASP Dependency Check provides the ability to generate a bill of materials and identify potential security risk.

Dependency check uses several pieces of evidence to determine the library names. You can add OWASP Dependency check as a plugin to the pom.xml of a Maven project for instance. The plugin will download information from public vulnerability databases and it will check if vulnerable libraries are used and will indicate which vulnerability was reported.

As part of a development pipeline, you can instruct the plugin to fail the build if there are violations that the development team was not aware of. Additionally you can use an xml file to waiver some of the violations. You should do so if the mentioned vulnerability cannot be exploited in your application.

In the parent pom.xml from WebGoat you can see an example:

```
<plugin>
        <groupId>org.owasp</groupId>
        <artifactId>dependency-check-maven</artifactId>
        <version>5.3.2</version>
        <configuration>
                <failBuildOnCVSS>7</failBuildOnCVSS>
                <skipProvidedScope>true</skipProvidedScope>
                <skipRuntimeScope>true</skipRuntimeScope>
                <suppressionFiles>
                        <suppressionFile>project-suppression.xml</suppressionFile>
                </suppressionFiles>
        </configuration>
        <executions>
                <execution>
                        <goals>
                                <goal>check</goal>
                        </goals>
                </execution>
        </executions>
</plugin>
```

And also an example of the suppressed violations.

```
<?xml version="1.0" encoding="UTF-8"?>
<suppressions xmlns="https://jeremylong.github.io/DependencyCheck/dependency-suppression.1.3.xsd">
    <suppress base="true">
        <cpe>cpe:/a:pivotal_software:spring_security</cpe>
        <cve>CVE-2018-1258</cve>
    </suppress>
    <suppress base="true"><!-- webgoat-server -->
        <cpe>cpe:/a:postgresql:postgresql</cpe>
        <cve>CVE-2018-10936</cve>
    </suppress>
</suppressions>
```

In the case of WebGoat, the plugin is activated when the following is run (owasp profile):

```
mvn clean install -Powasp
```

Below is a snippet of a report, which can be found in e.g. webgoat-container/target/dependency-check-report.html:

<figure><img src="../../../../.gitbook/assets/bill of material 1.png" alt=""><figcaption></figcaption></figure>
