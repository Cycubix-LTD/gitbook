---
title: "A2:2021 | Crypto Basics (4) | Cycubics Docs"
layout: default
nav_order: 4
parent: "A2:2021 | Cryptographic Failures | Cycubix Docs"
grand_parent: "WebGoat Labs | Web Application Security Essentials | Cycubix Docs"
---
# A2:2021 | Crypto Basics (4) | Cycubics Docs

### Plain Hashing <a href="#plain_hashing" id="plain_hashing"></a>

Hashing is a type of cryptography which is mostly used to detect if the original data has been changed. A hash is generated from the original data. It is based on irreversible cryptographic techniques. If the original data is changed by even one byte, the resulting hash is also different.

So in a way it looks like a secure technique. However, it is NOT and even NEVER a good solution when using it for passwords. The problem here is that you can generate passwords from dictionaries and calculate all kinds of variants from these passwords. For each password you can calculate a hash. This can all be stored in large databases. So whenever you find a hash that could be a password, you just look up the hash in the database and find out the password.

Some hashing algorithms should no longer be used: MD5, SHA-1 For these hashes it is possible to change the payload in such a way that it still results in the same hash. This takes a lot of computing power, but is still a feasible option.

For more information, please visit [NIST ](https://www.nist.gov/news-events/news/2022/12/nist-transitioning-away-sha-1-all-applications)website where you will be able to see the transition plan from the current limited use of SHA-1 into other approved hash functions. 

### Salted Hashes <a href="#salted_hashes" id="salted_hashes"></a>

Plain passwords should obviously not be stored in a database. And the same goes for plain hashes. The [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html) explains what should be used when password related information needs to be stored securely.

Salted hashes are a cryptographic technique used to enhance the security of hashed data, particularly passwords. They combine a user's password with a random value known as a "salt" before hashing it, making it significantly more difficult for attackers to use precomputed tables (rainbow tables) to crack the hashes.

### Assignment <a href="#assignment" id="assignment"></a>

Now let’s see if you can find what passwords matches which plain (unsalted) hashes.

<figure><img src="../../../../.gitbook/assets/Hashing (1).png" alt=""><figcaption></figcaption></figure>

**Solution**

* Go to WebGoat and copy the first Hash. 
* Open [Hashes.com](https://hashes.com/) and paste the hash. Click in the button "Submit & Identify". 

<figure><img src="../../../../.gitbook/assets/identify hashes hashes.com.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/identify hashes result md5.png" alt=""><figcaption></figcaption></figure>

* Copy the MD5 Hash, go to [MD5 Center](https://md5.gromweb.com/) and paste it. Select "reverse" and you will see the string. 

<figure><img src="../../../../.gitbook/assets/convert md5 to string.png" alt=""><figcaption></figcaption></figure>

* Type the word password into the box corresponding to the first hash. Regarding the second hash, copy it, and then go into Hashes.com to paste it. 
* You will see that the possible identification corresponds to SHA256. 

<figure><img src="../../../../.gitbook/assets/sha hash.png" alt=""><figcaption></figcaption></figure>

* On the same page, click on tje option "Decrypt Hashes".  You will receive the result. Go ahead and type the solution in WebGoat. 

<figure><img src="../../../../.gitbook/assets/solution with salted hashes.png" alt=""><figcaption></figcaption></figure>

