# Secure Hash Algorithms

In the past, many hash algorithms was proposed and used by software developers.

* **Old hash algorithms **like **MD5**, **SHA-0** and **SHA-1** were withdrawn due to cryptographic weaknesses \(collisions found\).
* **Don't use **MD5, SHA0 and SHA1! These hash functions are cryptographically **insecure**.
* You can find in Internet that **SHA1 collisions** can be practically generated and this results in algorithms for creating **fake digital signatures**, demonstrated by two different signed PDF documents which hold different content, but have the same hash value and the same digital signature. See [https://shattered.io](https://shattered.io).

**Modern cryptographic hash algorithms **are considered secure enough for most applications:

* **SHA-2 **is a family of functions: SHA-256 \(256 bits hash\), SHA-512 \(512 bits hash\), etc. SHA-2 is widely used and is considered strong enough for modern commercial applications. SHA-256 is used in the **Bitcoin** blockchain.
* By design, **more bits **at the hash output are expected to achieve **stronger security**. 128-bit hash functions are generally weaker than 256-bit hash functions, which are weaker than 512-bit hash functions. Thus, SHA-512 is stronger than SHA-256, so we can expect that for SHA-512 it is more unlikely to practically find a collision than for SHA-256.
* **SHA-3 **is considered more secure than SHA-2 \(SHA-256, SHA-384, SHA-512\) when the same hash length is used. For example, SHA3-256 provides more cryptographic strength than SHA-256 for the same hash length \(256 bits\). The **SHA-3** family of functions are also known as "**Keccak**" hashes. The hash function Keccak-256 is used in **Ethereum**.
* **RIPEMD-160 **is secure hash function, widely used in cryptography, e.g. in PGP and Bitcoin. The 160-bit variant is considered cryptographically stronger than the other variations like RIPEMD-128, RIPEMD-256 and RIPEMD-320.
* **BLAKE** / **BLAKE2 **/ **BLAKE2s **/ **BLAKE2b** is a family of fast, secure cryptographic hash functions. BLAKE has 256-bit \(BLAKE-256, BLAKE2s\) and 512-bit \(BLAKE-512, BLAKE2b\) variants.

As of Mar 2018, **no collisions are known **for: SHA256, SHA3-256, Keccak-256, BLAKE2s, RIPEMD160

* **Brute forcing **to find collision costs: 2^128 for SHA256 / SHA3-256 and 2^80 for RIPEMD160.
* Respectively, on a powerful enough quantum computer, it will cost less time: 2^256/3 and 2^160/3 respectively.

\* Learn more at: [https://z.cash/technology/history-of-hash-function-attacks.html](https://z.cash/technology/history-of-hash-function-attacks.html)

Play with hash functions online: [http://hash-functions.online-domain-tools.com](http://hash-functions.online-domain-tools.com/).

