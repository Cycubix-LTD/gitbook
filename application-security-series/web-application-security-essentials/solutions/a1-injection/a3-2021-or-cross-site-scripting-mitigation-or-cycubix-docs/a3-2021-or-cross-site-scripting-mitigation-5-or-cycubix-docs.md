---
title: "A3:2021 | Cross Site Scripting Mitigation (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A3:2021 | Cross Site Scripting Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting Mitigation (5) | Cycubix Docs

### Reflective XSS <a href="#reflective_xss" id="reflective_xss"></a>

See the HTML file below, which passes data to a JSP file.

```
<html>
   <body>
      <form action = "main.jsp" method = "POST">
         First Name: <input type = "text" name = "first_name">
         <br />
         Last Name: <input type = "text" name = "last_name" />
         <input type = "submit" value = "Submit" />
      </form>
   </body>
</html>
```

Here is the JSP file:

```
<html>

<head>
    <title>Using GET and POST Method to Read Form Data</title>
</head>

<body>
    <h1>Using POST Method to Read Form Data</h1>
    <table>
        <tbody>
            <tr>
                <td><b>First Name:</b></td>
                <td><%= request.getParameter("first_name")%></td>
            </tr>
            <tr>
                <td><b>Last Name:</b></td>
                <td>
                    <%= request.getParameter("last_name")%>
                </td>
            </tr>
        </tbody>
    </table>
</body>

</html>
```

As you can see the JSP file prints unfiltered user input which is never a good idea. You want people to access the page like this:

```
http://hostname.com/mywebapp/main.jsp?first_name=John&last_name=Smith
```

But what happens if someone uses this link:

```
http://hostname.com/mywebapp/main.jsp?first_name=<script>alert("XSS Test")</script>
```

#### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

Try to prevent this kind of XSS by escaping the URL parameters in the JSP file:

<figure><img src="../../../../../.gitbook/assets/xss mitigation 5.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Hint: You do not store the user input in this example. Try to encode the user's input right before you place it into the HTML document. We need to make use of JavaServer Pages Standard Tag Library (JSTL) and JSP Expression Language.
* We can also take a look at [OWASP Java Encoder Project](https://owasp.org/www-project-java-encoder/). One additional hint mentions that we should not forget to reference the tag libs and choose "e" as prefix.
* So we know we will be using OWASP Java Encoder Porject to mitigate XSS vulnerabilities. We will declare the use of a tag library with taglib in the JSP file. 

```
<%@ taglib uri="https://www.owasp.org/index.php/OWASP_Java_Encoder_Project" prefix="e" %>

```

* A table tag will create a table to display the form of data. 
* Tr Tags will define rows within the table. Td tags will define cells within each road. 
* Parameters `first_name` and `last_name` from the request, will  encode them using the OWASP Java Encoder, and then displays them in a table.
* Here is the code: 

```
<%@ taglib uri="https://www.owasp.org/index.php/OWASP_Java_Encoder_Project" prefix="e" %>
<!DOCTYPE html>
<html>
<head>
    <title>Using GET and POST Method to Read Form Data</title>
</head>
<body>
    <h1>Using POST Method to Read Form Data</h1>
    <table>
        <tbody>
            <tr>
                <td><b>First Name:</b></td>
                <td>${e:forHtml(param.first_name)}</td>
            </tr>
            <tr>
                <td><b>Last Name:</b></td>
                <td>${e:forHtml(param.last_name)}</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```

<figure><img src="../../../../../.gitbook/assets/webgoat xss 5 mitigation (1).png" alt=""><figcaption></figcaption></figure>
