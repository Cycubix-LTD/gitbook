---
description: The query in the code builds a dynamic query by concatenating a number making it susceptible to Numeric SQL injection. Learn more about Numeric SQL Injection.
title: "A3:2021 | SQL Injection Intro (10) | Cycubix Docs"
layout: default
nav_order: 10
parent: "A3:2021 | SQL Injection Intro | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Intro (10) | Cycubix Docs

### Try It! Numeric SQL injection <a href="#try_it_numeric_sql_injection" id="try_it_numeric_sql_injection"></a>

The query in the code builds a dynamic query as seen in the previous example. The query in the code builds a dynamic query by concatenating a number making it susceptible to Numeric SQL injection:

```
"SELECT * FROM user_data WHERE login_count = " + Login_Count + " AND userid = "  + User_ID;
```

Using the two Input Fields below, try to retrieve all the data from the users table.

Warning: Only one of these fields is susceptible to SQL Injection. You need to find out which, to successfully retrieve all the data.

#### Solution

* The User\_ID at the end is not part of the STRING so its going to be our vulnerable field. 
* We need to find statements that follows a technique for evaluating truth. We can insert 0 in the loging account and 1 OR 0=0. 
* Hint:  You do not need to insert any quotations into your injection-string.
*  **Login\_count**: `0`

<figure><img src="../../../../../.gitbook/assets/sql injection 9 3.png" alt=""><figcaption></figcaption></figure>



### Further training

Visit [**Cycubix.com**](https://cycubix.com/) to find out more about our [Application Security training courses](https://cycubix.com/training/). We also offer [(ISC)² Official training for CISSP, SSCP, CCSP and CSSLP certifications](https://cycubix.com/training/).
