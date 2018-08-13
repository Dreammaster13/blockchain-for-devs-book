# Cryptographic Hash Functions

In cryptography, **hash functions** transform **input data** of arbitrary size \(e.g. a text message\) to a **result** of fixed size \(e.g. 256 bits\), which is called **hash value** \(or hash code, message digest, or simply hash\). Hash functions \(hashing algorithms\) used in computer cryptography are known as "**cryptographic hash functions**". Examples of such functions are **SHA-256** and **SHA3-256**, which transform arbitrary input to 256-bit output.![](/assets/crypto-hash-function.jpg)As an **example**, we can take the cryptographic hash function `SHA-256` and calculate the hash value of certain text message:

```
SHA-256("hello") = "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
```

There is no efficient algorithm to find the input message \(in the above example `hello`\) from its hash value \(in the above example `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`\). It is well-known that cryptographic hash functions **cannot be reversed **back, so they are used widely to encode an input without revealing it \(e.g. encode a private key to a blockchain address without revealing the key\).

**Cryptographic hash functions **are widely used in cryptography, in computer programming and in blockchain systems.

