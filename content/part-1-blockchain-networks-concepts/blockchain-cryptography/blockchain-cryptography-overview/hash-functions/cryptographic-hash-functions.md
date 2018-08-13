# Cryptographic Hash Functions

In cryptography **hash functions** map **input data** of arbitrary size \(e.g. a text message\) to a **result** of fixed size, which is called **hash value** \(or hash code, message digest, or simply hash\). **Collisions** in cryptographic hash functions are **extremely unlikely** to happen, so crypto **hashes **are considered to almost uniquely identify their corresponding input.

![](/assets/crypto-hash-function.jpg)

Cryptographic hash functions are **irreversible by design**, which means that there is no fast algorithm to reproduce the input message from its hash value.

As an example, we can take the cryptographic hash function `SHA-256`:

```
SHA-256("hello") = "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
```

**Hash functions** are widely used in cryptography, in programming and in blockchain systems.



