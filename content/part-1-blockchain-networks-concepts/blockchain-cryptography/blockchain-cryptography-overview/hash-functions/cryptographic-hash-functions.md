# Cryptographic Hash Functions

In cryptography, **hash functions** transform **input data** of arbitrary size \(e.g. a text message\) to a **result** of fixed size \(e.g. 256 bits\), which is called **hash value** \(or hash code, message digest, or simply hash\). Hash functions \(hashing algorithms\) used in computer cryptography are known as "**cryptographic hash functions**". Examples of such functions are **SHA-256** and **SHA3-256**, which transform arbitrary input to 256-bit output.![](/assets/crypto-hash-function.jpg)

## Cryptographic Hash Functions - Examples

As an **example**, we can take the cryptographic hash function `SHA-256` and calculate the hash value of certain text message `hello`:

```
SHA-256("hello") =
  "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
```

There is no efficient algorithm to find the input message \(in the above example `hello`\) from its hash value \(in the above example `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`\). It is well-known that cryptographic hash functions **cannot be reversed **back, so they are used widely to encode an input without revealing it \(e.g. encode a private key to a blockchain address without revealing the key\).

As another **example**, we can take the cryptographic hash function `SHA3-512` and calculate the hash value of the same text message `hello`:

```
SHA3-512("hello") = "75d527c368f2efe848ecf6b073a36767800805e9eef2b1857d5f984f036eb6df891d75f72d9b154518c1cd58835286d1da9a38deba3de98b5a53e5ed78a84976"
```

## Cryptographic Hash Functions - Live Demo

**Play** with most popular cryptographic hash functions **online**: [https://www.fileformat.info/tool/hash.htm](https://www.fileformat.info/tool/hash.htm).

![](/assets/hash-functions-online.png)**Cryptographic hash functions **are widely used in cryptography, in computer programming and in blockchain systems.

