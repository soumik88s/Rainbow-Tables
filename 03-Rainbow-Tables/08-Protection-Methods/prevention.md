# Password Protection Methods

## 1. Introduction

Rainbow tables can be used to recover passwords from stolen password hashes when the hashes are vulnerable to precomputed attacks.

Developers can reduce this risk by using secure password-storage methods.

## 2. What Is a Salt?

A salt is a unique, randomly generated value added to a password before hashing.

### Why use salts?

- Every user gets a different salt.
- Identical passwords produce different stored hashes when different salts are used.
- Precomputed rainbow tables become ineffective against properly salted password hashes.
- Attackers must perform separate password guesses for each salt.

**Example:**

```text
Password: hello123

User A:
Salt: random_salt_A
Hash: Hash(hello123 + random_salt_A)

User B:
Salt: random_salt_B
Hash: Hash(hello123 + random_salt_B)
```

The resulting hashes will be different.

## 3. Use Secure Password-Hashing Algorithms

Not all hashing algorithms are suitable for password storage.

### Recommended algorithms

| Algorithm | Purpose |
|---|---|
| Argon2id | Modern password hashing; memory-hard |
| bcrypt | Password hashing designed to be computationally expensive |
| scrypt | Password hashing designed to use significant memory |
| PBKDF2 | Password-based key derivation using repeated hashing |

**Important:** SHA-256 and MD5 are general-purpose hash functions. They should not be used alone for storing user passwords.

## 4. Use Strong Passwords

Strong passwords make guessing attacks more difficult.

Recommended practices:

- Use long passwords.
- Avoid names and birthdays.
- Avoid common dictionary words.
- Use unique passwords for different accounts.
- Consider using a password manager.

## 5. Enable Multi-Factor Authentication (MFA)

Multi-factor authentication adds another layer of security.

Even if an attacker discovers a password, they may still need another authentication factor.

Examples:

- Authenticator applications
- Hardware security keys
- Passkeys

## 6. Protect Stored Password Data

Developers should:

- Never store passwords as plain text.
- Use a unique random salt for every password.
- Use a reputable password-hashing library.
- Choose an appropriate work factor.
- Restrict access to password databases.
- Use HTTPS for login and registration pages.
- Regularly update authentication systems.

## 7. Rainbow Tables vs. Salted Hashes

| Feature | Unsalted Hash | Salted Hash |
|---|---|---|
| Unique salt | No | Yes |
| Same password produces the same hash | Usually yes | Not when salts differ |
| Vulnerable to precomputed rainbow-table attacks | More vulnerable | Strongly mitigated |
| Separate guesses needed per salt | No | Yes |

## 8. Conclusion

Rainbow table attacks demonstrate why secure password storage is important.

Using unique random salts, modern password-hashing algorithms such as Argon2id, and strong authentication practices makes password databases much harder to attack.

**Key takeaway:** Never store plain-text passwords or rely on fast general-purpose hashes alone for password storage.
