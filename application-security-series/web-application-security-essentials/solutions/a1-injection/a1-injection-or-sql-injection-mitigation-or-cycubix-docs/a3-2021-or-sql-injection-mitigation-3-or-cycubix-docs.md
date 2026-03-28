---
title: "A3:2021 | SQL Injection Mitigation (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (3) | Cycubix Docs

### Parameterized Queries - Java Snippet <a href="#parameterized_queries_java_snippet" id="parameterized_queries_java_snippet"></a>

```
public static bool isUsernameValid(string username) {
    RegEx r = new Regex("^[A-Za-z0-9]{16}$");
    return r.isMatch(username);
}

// java.sql.Connection conn is set elsewhere for brevity.
PreparedStatement ps = null;
RecordSet rs = null;
try {
    pUserName = request.getParameter("UserName");
    if ( isUsernameValid (pUsername) ) {
        ps = conn.prepareStatement("SELECT * FROM user_table WHERE username = ? ");
        ps.setString(1, pUsername);
        rs = ps.execute();
        if ( rs.next() ) {
            // do the work of making the user record active in some way
        }
    } else {
        // handle invalid input
    }
}
catch (...) { // handle all exceptions ... }
```

### Important <a href="#important" id="important"></a>

Use the prepared statement correctly; parameters should be set with `ps.set..()` and DO NOT use the following statement:

```
String insertStatement = "INSERT INTO USERS (id, name, email) VALUES (%s, %s, %s)".format("1", "webgoat", "webgoat@owasp.org");
PreparedStatement statement = conn.prepareStatement(insertStatement);
statement.executeUpdate();
```

(For the sake of the example, we assume that the passed values are based on user input). The example above is not the correct way to use a prepared statement, use:

```
PreparedStatement statement = conn.prepareStatement("INSERT INTO USERS (id, name, email) VALUES (?, ?, ?)");
statement.setString(1, "1");
statement.setString(2, "webgoat");
statement.setString(3, "webgoat@owasp.org");
statement.executeUpdate();
```
