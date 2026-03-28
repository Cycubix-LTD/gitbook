---
title: "A7:2021 | Secure Passwords (6) | Cycubix Docs"
layout: default
nav_order: 6
parent: "A7:2021 | Secure Passwords | Cycubix Docs"
grand_parent: "A7:2021 | Identity and Authentication Failure | Cycubix Docs"
---
# A7:2021 | Secure Passwords (6) | Cycubix Docs

#### Storing passwords <a href="#storing_passwords" id="storing_passwords"></a>

After a strong and secure password was created, it also has to be stored securely. The NIST gives recommendations on how applications should handle passwords and how to store them securely.

**How should a password be stored?**

* first of all: **use encryption and a protected channel for requesting passwords**\
  The verifier shall use approved encryption and an authenticated protected channel to resist eavesdropping and MitM (Man-in-the-middle) attacks when requesting memorized secrets.
* **resistant to offline attacks**\
  Passwords should be stored in a form that is resistant to offline attacks.
* **use salts**\
  Passwords should be salted before storing them. The salt shall have at least 32 bits in length and should be chosen arbitrarily to minimize salt value collisions among stored hashes.
* **use hashing**\
  Before storing a password, it should be hashed with a one-way key derivation function. The function inputs the password, salt, and cost factor and then generates a password hash.\
  Examples of suitable key derivation functions:
  * Password-based Key Derivation Function 2 ([PBKDF2](https://pages.nist.gov/800-63-3/sp800-63b.html#SP800-132)) (as large as possible ⇒ at least 10.000 iterations)
  * [BALLOON](https://pages.nist.gov/800-63-3/sp800-63b.html#SP800-132)
  * The key derivation function shall use an approved one-way function such as:
    * Keyed Hash Message Authentication Code ([HMAC](https://pages.nist.gov/800-63-3/sp800-63b.html#FIPS198-1))
    * any approved hash function in [SP 800-107](https://pages.nist.gov/800-63-3/sp800-63b.html#SP800-107)
    * Secure Hash Algorithm 3 ([SHA-3](https://pages.nist.gov/800-63-3/sp800-63b.html#FIPS202))
    * [CMAC](https://pages.nist.gov/800-63-3/sp800-63b.html#SP800-38B)
    * Keccak Message Authentication Code (KMAC)
    * Customizable SHAKE (cSHAKE)
    * [ParallelHash](https://pages.nist.gov/800-63-3/sp800-63b.html#SP800-185)
* **memory hard key derivation function**\
  Use memory-hard key derivation functions to increase the needed cost further to perform attacks.
* **high cost factor**\
  The key derivation function’s cost factor (iteration count) should be as large as verification server performance will allow. (at least 10.000 iterations)
