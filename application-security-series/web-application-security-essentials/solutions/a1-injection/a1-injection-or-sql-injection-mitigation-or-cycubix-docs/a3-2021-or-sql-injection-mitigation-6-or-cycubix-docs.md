---
title: "A3:2021 | SQL Injection Mitigation (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (6) | Cycubix Docs

### Try it! Writing safe code <a href="#try_it_writing_safe_code" id="try_it_writing_safe_code"></a>

Now it is time to write your own code! Your task is to use JDBC to connect to a database and request data from it.

Java Database Connectivity (JDBC) is a Java-based API that enables Java applications to interact with databases. JDBC provides methods for querying and updating data in a database. Here’s a more detailed overview of JDBC and an example of how to use it to connect to a database and request data from it.

**Requirements:**

* connect to a database
* perform a query on the database which is immune to SQL injection attacks
* your query needs to contain at least one string parameter

**Some tips before you start:**\
For connecting to the database, you can simply assume the constants **DBURL**, **DBUSER** and **DBPW** as given.

\
The content of your query does not matter, as long as the SQL is valid and meets the requirements.

\
All the code you write gets inserted into the main method of a Java class with the name "TestClass" that already imports **java.sql.**\* for you.

Not creative enough to think of your own query? How about you try to retrieve the data of a user with a specific name from a fictional database table called **users**.

For example; the following code would compile without any error (but of course does not meet the requirements to complete this lesson).

```
try {
    Connection conn = null;
    System.out.println(conn);   //should output 'null'
} catch (Exception e) {
    System.out.println("Oops. Something went wrong!");
}
```

Use your knowledge and write some valid code from scratch in the editor window down below! (if you cannot type there it might help to adjust the size of your browser window once, then it should work):

**Solution**

* The code will handle database connections properly, use parameterized queries to prevent SQL injection, and include error handling. 
* You will have to think about creating a code that has three blocks: 

**Try Block**: The code to establish the connection and perform database operations is placed inside the try block.

**Catch Block**: Catches any `SQLException` that might occur while connecting to the database or executing queries. This prevents the program from crashing and allows you to handle the error appropriately (e.g., logging the error, displaying a message to the user).

**Finally Block**: Ensures that the database connection is closed regardless of whether an exception was thrown. This is important for resource management to avoid potential memory leaks and ensure the connection is properly closed.

Complete the window with:

```
try {  
     Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);  
     PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE name = ?");  
     ps.setString(1, "Admin");  
     ps.executeUpdate();  
} catch (Exception e) {  
     System.out.println("Oops. Something went wrong!");  
}
```



**Try Block- Establishing the connection to the databse**

```
try {  
     Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);  
     PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE name = ?");  
     ps.setString(1, "Admin");  
     ps.executeUpdate(); 
```

**Catch Block- Handling any exceptions that might occur within the try block. If an exception is thrown, this block will catch it and execute the code inside it**.

```
} catch (Exception e) {  
     System.out.println("Oops. Something went wrong!");  
}
```

Final Block- ensures that resources are properly closed, even if an exception occurs. It is generally used to close the connection and other resources.
