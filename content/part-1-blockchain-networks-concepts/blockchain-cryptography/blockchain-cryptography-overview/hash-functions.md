# Hashing and Hash Functions

In computer programming **hash functions **map text values to numbers. Usually different input text maps to different output number, but sometimes a **collision** may happen \(different input with same output\).

![](/assets/hash-function.jpg)

In cryptography **hash functions** map input data \(or text message\) of arbitrary size to a result of fixed size, which is called **hash value** \(or hash code, message digest, or simply hash\). **Collisions** in cryptographic hash functions are **extremely unlikely** to happen, so crypto **hashes **are considered to almost uniquely identify their corresponding input.

![](/assets/crypto-hash-function.jpg)

Cryptographic hash functions are **irreversible by design**, which means that there is no fast algorithm to reproduce the input message from its hash value.

**Hash functions** are widely used in cryptography, in programming and in blockchain systems.

