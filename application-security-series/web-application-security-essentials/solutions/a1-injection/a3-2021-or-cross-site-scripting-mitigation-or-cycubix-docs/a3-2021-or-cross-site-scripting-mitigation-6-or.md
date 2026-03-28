---
title: "A3:2021 | Cross Site Scripting Mitigation (6) |"
layout: default
nav_order: 6
parent: "A3:2021 | Cross Site Scripting Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Cross Site Scripting Mitigation (6) |

### Stored XSS <a href="#stored_xss" id="stored_xss"></a>

One way to prevent stored XSS is the usage of [OWASP AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project). AntiSamy can produce a "clean" string based on an adjustable policy file.

See the java class below, which saves a comment into a database.

```
public class MyCommentDAO {

    public static void addComment(int threadID, int userID, String newComment) {

                String sql = "INSERT INTO COMMENTS(THREADID, USERID, COMMENT) VALUES(?,?,?);";

                try {
                        PreparedStatement stmt = connection.prepareStatement(sql);

                        stmt.setInt(1, threadID);
                        stmt.setInt(2, userID);
                        stmt.setString(3, newComment);

                        stmt.executeUpdate();
                } catch (SQLException e) {
                        e.printStackTrace();
                }
        }
}
```

And here is a Java class that uses the addComment function

```
import org.owasp.validator.html.*;
import MyCommentDAO;

public class AntiSamyController {
    ...
    public void saveNewComment(int threadID, int userID, String newComment){
        MyCommentDAO.addComment(threadID, userID, newComment);
    }
    ...
}
```

As you can see the Java file stores unfiltered user input into the database. You have the whole malicious code stored in your database now.

### It is your turn! <a href="#it_is_your_turn" id="it_is_your_turn"></a>

Try to prevent this kind of XSS by creating a clean string inside the saveNewComment() function. Use the "antisamy-slashdot.xml" as a policy file for this example:

<figure><img src="../../../../../.gitbook/assets/xss mitigation 6.png" alt=""><figcaption></figcaption></figure>

**Solution**

* Hints: Try to have a look at the AntiSamy documentation.
* Looking at the documentation will allow us to add the necessary imports. 
* We also need to create a policy file: you can find it in this repository. [https://github.com/nahsra/antisamy](https://github.com/nahsra/antisamy)
* When you implement the code, dpeloy and test the application be ensure that user inputs are sanitized correctly, thus mitigating XSS vulnerabilities.

The solution code is the following: 

```
import org.owasp.validator.html.*;  
import MyCommentDAO;  
  
public class AntiSamyController {  
     public void saveNewComment(int threadID, int userID, String newComment){  
         Policy p = Policy.getInstance("antisamy-slashdot.xml");  
         AntiSamy as = new AntiSamy();  
         CleanResults cr = as.scan(newComment, p, AntiSamy.DOM);  
         MyCommentDAO.addComment(threadID, userID, cr.getCleanHTML());  
     }  
}  
```

<figure><img src="../../../../../.gitbook/assets/xss mitigation samy (1).png" alt=""><figcaption></figcaption></figure>



