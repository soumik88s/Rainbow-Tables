# How Rainbow Tables Work

## 1. Introduction

Rainbow tables use a time-memory trade-off technique to make certain password recovery operations more efficient.

They work through precomputed chains involving cryptographic hash functions and reduction functions.

## 2. Hash Function

A hash function converts an input value into a fixed-length hash.

Example:

```python
import hashlib

password = "apple"

result = hashlib.sha256(
    password.encode()
).hexdigest()

print(result)
```

The same input produces the same SHA-256 hash.

## 3. Reduction Function

A reduction function maps a hash value into a possible plaintext candidate.

Important:

- A reduction function is not a decryption function.
- It does not reverse the original hash.
- Different reduction functions can generate different candidate values.

## 4. Hash Chains

A hash chain is a sequence of alternating hash and reduction operations.

The general process is:

1. Start with a candidate password.
2. Generate its hash.
3. Apply a reduction function.
4. Generate another hash from the new candidate.
5. Repeat the process.
6. Store the starting value and final endpoint.

## 5. Chain Endpoints

Instead of storing every intermediate value, rainbow tables store selected chain information, particularly starting points and endpoints.

This helps reduce storage requirements.

## 6. Time-Memory Trade-Off

Rainbow tables balance two resources:

- Time: Computation required during lookup.
- Memory: Storage required for precomputed chains.

Reducing memory generally requires additional computation.

## 7. Collision and Chain Merging

Two different chains can sometimes reach the same intermediate value.

This is called a collision and can cause chains to merge.

Rainbow tables use different reduction functions at different chain positions to reduce the chain-merging problem.

## 8. Limitations

- Chain collisions can occur.
- Precomputation takes time.
- Coverage depends on the candidate password space.
- Different hash algorithms require different tables.
- Unique salts make reusable precomputed tables impractical.

## 9. Conclusion

Understanding hash functions, reduction functions, chains, and endpoints is essential to understanding rainbow table construction.

These concepts demonstrate the importance of modern password-storage security.

**Purpose:** Educational cybersecurity research and authorized laboratory demonstrations.
