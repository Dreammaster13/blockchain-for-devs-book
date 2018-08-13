# Cryptographic Hash Functions

In cryptography, **hash functions** transform **input data** of arbitrary size \(e.g. a text message\) to a **result** of fixed size \(e.g. 256 bits\), which is called **hash value** \(or hash code, message digest, or simply hash\). Hash functions \(hashing algorithms\) used in computer cryptography are known as "**cryptographic hash functions**". Examples of such functions are **SHA-256** and **SHA3-256**, which transform arbitrary input to 256-bit output.![](/assets/crypto-hash-function.jpg)As an **example**, we can take the cryptographic hash function `SHA-256` and calculate the hash value of certain text message:

```
SHA-256("hello") = "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
```

There is no efficient algorithm to find the input message \(in the above example `hello`\) from its hash value \(in the above example `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`\).

## Cryptographic Hash Functions and Collisions

**Collisions** in the cryptographic hash functions are **extremely unlikely** to happen, so crypto **hashes **are considered to almost uniquely identify their corresponding input. Moreover, it is extremely hard to find an input message that hashes to given value.

Cryptographic hash functions are **one-way hash functions**, which are **infeasible to invert**. The chance to find a collision for a strong cryptographic hash function \(like SHA-256\) is extremely little. Let's define this in more details:

* Let's have hash value `h` =`hash(p)` for certain strong cryptographic hash function `hash`.
* It is expected to be **extremely hard** to find an input `p'`, such that `hash(p')` = `h`.
* For most modern strong cryptographic hash functions there are **no known collisions**.

**Cryptographic hash functions** are widely used in cryptography, in computer programming and in blockchain systems.

