---
title: "A3:2021 | SQL injection Mitigation (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL injection Mitigation (5) | Cycubix Docs

### Try it! Writing safe code <a href="#try_it_writing_safe_code" id="try_it_writing_safe_code"></a>

You can see some code down below, but the code is incomplete. Complete the code, so that it’s no longer vulnerable to a SQL injection! Use the classes and methods you have learned before.

The code has to retrieve the status of the user based on the name and the mail address of the user. Both the name and the mail are in the string format. 

<figure><img src="../../../../../.gitbook/assets/sql injection 5.png" alt=""><figcaption></figcaption></figure>



#### Solution

* The first hint indicates "First establish a connection, after that you can create a statement.". Then the first imput could be getConnection. 
*   The second  hint established that "For every data type there is a method to insert values into a wildcard symbol in a statement". From lesson 1 "Inmutable Queries" we know that "

    ```
    PreparedStatement statement = connection.prepareStatement(query);
    ```
*   Then we can go ahead and imput: 

    ```
    PreparedStatement statement and .prepareStatement
    ```
* Given that the value of name and email are based on user imput, we could use ? in the PreparedStatement. (Go into Parameterized queries if any doubt). We will be using ? as a placeholder. 
*   For the last two strings we can use 

    ```
    statement.setString(1, "1"); statement.setString(2, "2")

    ```
