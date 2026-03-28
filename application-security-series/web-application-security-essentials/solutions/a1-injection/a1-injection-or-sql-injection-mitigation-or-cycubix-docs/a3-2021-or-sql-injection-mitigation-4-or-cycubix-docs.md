---
title: "A3:2021 | SQL Injection Mitigation (4) | Cycubix Docs"
layout: default
nav_order: 4
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (4) | Cycubix Docs

### Parameterized Queries - Java Example <a href="#parameterized_queries_java_example" id="parameterized_queries_java_example"></a>

```
public static String loadAccount() {
  // Parser returns only valid string data
  String accountID = getParser().getStringParameter(ACCT_ID, "");
  String data = null;
  String query = "SELECT first_name, last_name, acct_id, balance FROM user_data WHERE acct_id = ?";
  try (Connection connection = dataSource.getConnection()) {
       PreparedStatement statement = connection.prepareStatement(query)) {
     statement.setString(1, accountID);
     ResultSet results = statement.executeQuery();
     if (results != null && results.first()) {
       results.last(); // Only one record should be returned for this query
       if (results.getRow() <= 2) {
         data = processAccount(results);
       } else {
         // Handle the error - Database integrity issue
       }
     } else {
       // Handle the error - no records found }
     }
  } catch (SQLException sqle) {
    // Log and handle the SQL Exception }
  }
  return data;
}
```
