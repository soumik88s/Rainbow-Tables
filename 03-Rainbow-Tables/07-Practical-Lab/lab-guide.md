# Practical Python Lab – Rainbow Tables

## 1. Lab Introduction

This practical laboratory demonstrates the basic concepts behind rainbow tables using Python.

We will explore SHA-256 hashing, reduction functions, hash chains, and endpoint storage.

**Objective:** Understand the time-memory trade-off concept through a small educational experiment.

## 2. Requirements

- Python 3.x
- Visual Studio Code (recommended)
- Basic Python knowledge

## 3. Install Python

Download Python from:

https://www.python.org/downloads/

Verify the installation:

```bash
python --version
```

## 4. Create a SHA-256 Hash

Python provides the built-in hashlib library.

Example:

```python
import hashlib

password = "hello123"

password_hash = hashlib.sha256(
    password.encode("utf-8")
).hexdigest()

print("Password:", password)
print("SHA-256:", password_hash)
```

## 5. Understanding Hash Chains

A hash chain repeatedly applies two operations:

1. Hash a candidate.
2. Apply a reduction function to generate another candidate.

This process continues for a specified number of steps.

A reduction function is not a decryption function. It simply maps a hash to a candidate in a defined search space.

## 6. Educational Rainbow Chain Demonstration

The following Python example creates small hash chains using a predefined candidate list.

```python
import hashlib

# Small educational candidate space
candidates = [
    "apple",
    "banana",
    "mango",
    "orange",
    "grape",
    "lemon"
]

def generate_hash(password):
    return hashlib.sha256(
        password.encode("utf-8")
    ).hexdigest()

def reduce_hash(hash_value, position):
    number = int(hash_value[:8], 16)
    index = (number + position) % len(candidates)
    return candidates[index]

def generate_chain(start, chain_length=5):
    current = start

    for position in range(chain_length):
        hashed = generate_hash(current)
        current = reduce_hash(hashed, position)

    return current

# Generate educational chains
table = {}

for start in candidates:
    endpoint = generate_chain(start)
    table[start] = endpoint

print("Educational Hash Chains")

for start, endpoint in table.items():
    print(start, "->", endpoint)
```

## 7. Understanding the Output

The program:

- Starts with a sample candidate.
- Generates a SHA-256 hash.
- Applies a reduction function.
- Repeats the process.
- Stores the final endpoint.

The resulting structure demonstrates the basic concept of chain generation.

**Important:** This is a simplified hash-chain demonstration, not a complete production rainbow table implementation. It does not implement rainbow-table lookup or guarantee password recovery.

## 8. Practical Experiments

Try changing:

- The candidate list.
- The chain length.
- The reduction function.
- The number of starting candidates.

Observe how the generated endpoints change.

## 9. Security Lessons

This laboratory demonstrates why precomputed hash structures are possible.

Modern password-storage systems use unique salts and computationally expensive password hashing algorithms to make these attacks less practical.

## 10. Conclusion

This laboratory introduces the fundamental concepts behind rainbow table construction using Python.

It provides a foundation for understanding hash chains, reduction functions, and the time-memory trade-off.

**Lab type:** Educational cybersecurity demonstration using sample data.
