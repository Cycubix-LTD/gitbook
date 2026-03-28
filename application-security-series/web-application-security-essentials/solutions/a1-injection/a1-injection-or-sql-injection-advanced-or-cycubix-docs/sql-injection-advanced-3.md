---
title: "A3:2021 | SQL Injection Advanced (3) | Cycubix Docs"
layout: default
nav_order: 3
parent: "A3:2021 | SQL Injection Advanced | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Advanced (3) | Cycubix Docs

### Try It! Pulling data from other tables <a href="#try_it_pulling_data_from_other_tables" id="try_it_pulling_data_from_other_tables"></a>

The input field below is used to get data from a user by their last name.\
 The table is called 'user\_data':

```
CREATE TABLE user_data (userid int not null,
                        first_name varchar(20),
                        last_name varchar(20),
                        cc_number varchar(30),
                        cc_type varchar(10),
                        cookie varchar(20),
                        login_count int);
```

Through experimentation you found that this field is susceptible to SQL injection. Now you want to use that knowledge to get the contents of another table.<br>

The table you want to pull data from is:

```
CREATE TABLE user_system_data (userid int not null primary key,
			                   user_name varchar(12),
			                   password varchar(10),
			                   cookie varchar(30));
```

**6.a)** Retrieve all data from the table\
 **6.b)** When you have figured it out…​. What is Dave’s password?

Note: There are multiple ways to solve this Assignment. One is by using a UNION, the other by appending a new SQl statement. Maybe you can find both of them.

**Solution**

* In the hints of the exercise, it is stated that we should use the `UNION` command. This commend requires that both SELECT statements involved return the same number of columns with compatible data types in the same order.
* When we select the user\_data table we notice that there are more columns than the user\_system\_data table. 
* Because of the difference in the columns, we will concatenate the two statements and select userid, user\_name, password and cookies and create column A, B and 1 from user\_systrem\_data. 

**SELECT \* FROM user\_data WHERE last\_name = '' UNION SELECT 1, user\_name, password, cookie, 'A', 'B', 1 from user\_system\_data;--'**

We do this to have the same amount of columns than the user\_data table. If a column needs a String you could substitute something like 'a String' for it. For integers you could substitute a 1.

* You will be able to retrieve the data from all users and Dave's password. 

<figure><img src="../../../../../.gitbook/assets/solution sql advanced 1.png" alt=""><figcaption></figcaption></figure>

* How do we know that Dave's password is "passWorD"?, because from our Query we can follow the order or the values: user\_name, password, cookie, etc. 

