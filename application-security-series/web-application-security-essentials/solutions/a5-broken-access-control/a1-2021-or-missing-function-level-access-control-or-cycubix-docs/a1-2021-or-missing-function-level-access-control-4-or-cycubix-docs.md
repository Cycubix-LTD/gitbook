---
title: "A1:2021 | Missing Function Level Access Control (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A1:2021 | Missing Function Level Access Control | Cycubix Docs"
grand_parent: "A1:2021 | Broken Access Control | Cycubix Docs"
---
# A1:2021 | Missing Function Level Access Control (4) | Cycubix Docs

**The company fixed the problem, right?**

The company found out the endpoint was a bit too open, they made an emergency fixed and not only admin users can list all users.

Start with the information you already gathered (hidden menu items) to see if you can pull the list of users and then provide the 'hash' for Jerry’s account.

<figure><img src="../../../../../.gitbook/assets/missing function level access 4.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Remember Jerry's hash from the previous exercise? .  The exercise likely involves understanding how to generate a secure hash using a combination of a password, salt, and username.
* We tried to access the endpoint through Admin privileges but we couldn't. So let's break down the solution Code to solve this: 

```
import java.nio.charset.StandardCharsets;
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.util.Base64;

public class Main{
    public static void main(String[] args){
        // SVtOlaa+ER+w2eoIIVE5/77umvhcsh5V8UyDLUa1Itg=
        
        String password = "doesnotreallymatter";
        String username = "Jerry";
        String passwordSaltWeak = "DeliberatelyInsecure1234";
        String passwordSaltStrong = "DeliberatelyInsecure1235";

        try{
            MessageDigest md = MessageDigest.getInstance("SHA-256");
            String salted = password + passwordSaltStrong + username;
            byte[] hash = md.digest(salted.getBytes(StandardCharsets.UTF_8));
            System.out.println(Base64.getEncoder().encodeToString(hash));
        }catch(Error e){

        } catch (NoSuchAlgorithmException e) {
            throw new RuntimeException(e);
        }
    }
}
```

* In this code we are using a strong salt (`DeliberatelyInsecure1235`), combining the password, salt, and username to create a single string, generating a SHA-256 hash from the combined string, and encoding the hash to a base64 string for easy display or storage.
* The Main method class contains the entry point of the program. The variables are: 

`String password = "doesnotreallymatter";`: The password used (does not need to be real for hashing).

`String username = "Jerry";`: The username used in the exercise.

`String passwordSaltWeak = "DeliberatelyInsecure1234";`: An example of a weak salt.

`String passwordSaltStrong = "DeliberatelyInsecure1235";`: An example of a strong salt.

Use `MessageDigest` to get an instance of `SHA-256`.

* Save the code as a Java File "Main".  Open command prompt to compile the file. 

<figure><img src="../../../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

* Copy and paste the hash for Jerry in WebGoat. 

<figure><img src="../../../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

**Troubleshooting**

**Compiling the Code- Visual Code**

**Environment related issues**

* Ensure the JDK is correctly installed and the environment variables are set
* Ensure you have the Java Extension Pack installed.
* Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`), type `Java: Configure Java Runtime`, and ensure the correct JDK is selected.

**Syntax related issues**

* Make sure you name you r Java file as Main. If add another term do not leave spaces in between. The syntax must be correct in order to compile the file. 
* How to compile it? 
* Open a terminal or command prompt. 
* Navigate to the directory where your Java file (Main.java) is located.
* Compile the Java file using the javac command: javac Main.java
* This command will compile the Main.java file and generate a corresponding .class file.
* Run the Java Program: Once the Java file has been compiled successfully, you can run the program using the java command: java Main
* Make sure to specify the name of the class containing the main method (in this case, Main) without the .java extension.
* By following these steps, you should be able to compile and run the Java program without encountering an error message.
* This should print the Base64-encoded hash string generated from the provided input



