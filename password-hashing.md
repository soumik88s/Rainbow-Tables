# Understanding Password Hashing

## 1. What Is Password Hashing?

Password hashing is a process that converts a password into a fixed-length string using a mathematical function called a hash function.

A hash function is designed to be one-way, meaning the original password cannot practically be recovered directly from its hash.

## 2. How Does Password Hashing Work?

The basic process:

1. A user enters a password.
2. The password is passed into a hash function.
3. The hash function generates a hash value.
4. The system stores the hash instead of the original password.
5. During login, the entered password is checked against the stored password hash.

## 3. Example

Sample password:

`hello123`

Example SHA-256 hash:

`f22fbd7f1f7f7b8b5b2f1b9c6c1b0e9b`

Note: This is an illustrative placeholder, not the actual SHA-256 output.

## 4. Common Hashing Algorithms

| Algorithm | Description |
|---|---|
| MD5 | Legacy hash algorithm; unsuitable for password storage |
| SHA-1 | Legacy algorithm; unsuitable for password storage |
| SHA-256 | Cryptographic hash function |
| bcrypt | Password hashing algorithm |
| scrypt | Memory-hard password hashing function |
| Argon2id | Modern password hashing algorithm |

## 5. What Is a Salt?

A salt is a unique random value added to a password before hashing.

Salts help prevent attackers from using precomputed rainbow tables against password databases.

## 6. Connection to Rainbow Tables

Rainbow tables exploit the weaknesses of unsalted, fast password hashes.

When each password has a unique salt, attackers cannot directly reuse one precomputed table for every password.

## 7. Conclusion

Password hashing is an important part of cybersecurity. Using modern password hashing algorithms with unique salts helps protect user credentials.

**Security recommendation:** Use Argon2id, bcrypt, or scrypt for password storage rather than general-purpose fast hash functions.
