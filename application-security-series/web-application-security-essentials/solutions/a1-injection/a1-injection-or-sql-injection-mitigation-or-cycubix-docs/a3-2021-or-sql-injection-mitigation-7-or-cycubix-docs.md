---
title: "A3:2021 | SQL Injection Mitigation (7) | Cycubix Docs"
layout: default
nav_order: 7
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (7) | Cycubix Docs

### Parameterized Queries - .NET <a href="#parameterized_queries_net" id="parameterized_queries_net"></a>

```
public static bool isUsernameValid(string username) {
	RegEx r = new Regex("^[A-Za-z0-9]{16}$");
	Return r.isMatch(username);
}

// SqlConnection conn is set and opened elsewhere for brevity.
try {
	string selectString = "SELECT * FROM user_table WHERE username = @userID";
	SqlCommand cmd = new SqlCommand( selectString, conn );
	if ( isUsernameValid( uid ) ) {
		cmd.Parameters.Add( "@userID", SqlDbType.VarChar, 16 ).Value = uid;
		SqlDataReader myReader = cmd.ExecuteReader();
		if ( myReader ) {
			// make the user record active in some way.
			myReader.Close();
		}
	} else { // handle invalid input }
}
catch (Exception e) { // Handle all exceptions... }
```
