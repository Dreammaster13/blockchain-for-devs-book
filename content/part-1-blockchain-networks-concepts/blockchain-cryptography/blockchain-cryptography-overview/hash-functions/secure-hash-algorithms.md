# Secure Hash Algorithms

In the past, many **cryptographic hash algorithms** were proposed and used by software developers. Some of them was broken, some are still considered secure. Let's review the most widely used cryptographic hash functions \(algorithms\).

**Old hash algorithms **like **MD5**, **SHA-0** and **SHA-1** were withdrawn due to **cryptographic weaknesses** \(collisions found\).

* **Don't use MD5**, **SHA0** and **SHA1**! All these hash functions are proven to be cryptographically **insecure**.
* You can find in Internet that **SHA1 collisions** can be practically generated and this results in algorithms for creating **fake digital signatures**, demonstrated by two different signed PDF documents which hold different content, but have the same hash value and the same digital signature. See [https://shattered.io](https://shattered.io).

**Modern cryptographic hash algorithms **are considered secure enough for most applications:

* **SHA-2 **is a family of strong cryptographic hash functions: **SHA-256** \(256 bits hash\), **SHA-512** \(512 bits hash\), etc.
  * **SHA-2** is widely used and is considered cryptographically strong enough for modern commercial applications.
  * SHA-256 is widely used in the **Bitcoin** blockchain, e.g. for identifying the transaction hashes and for the proof-of-work mining performed by the miners.
* By design, **more bits **at the hash output are expected to achieve **stronger security**. As general rule, 128-bit hash functions are weaker than 256-bit hash functions, which are weaker than 512-bit hash functions. Thus, SHA-512 is stronger than SHA-256, so we can expect that for SHA-512 it is more unlikely to practically find a collision than for SHA-256.
* **SHA-3 **is considered **more secure than SHA-2** \(SHA-256, SHA-384, SHA-512\) for the same hash length. For example, SHA3-256 provides more cryptographic strength than SHA-256 for the same hash length \(256 bits\). The **SHA-3** family of functions are also known as "**Keccak**" hashes. The hash function **Keccak-256** is used in **Ethereum**.
* **RIPEMD-160 **is secure hash function, widely used in cryptography, e.g. in PGP and Bitcoin.
  * The 160-bit variant is considered cryptographically stronger than the other variations like RIPEMD-128, RIPEMD-256 and RIPEMD-320.
  * SHA-256 and SHA3-256 are more stronger than RIPEMD-160, due to higher bit length and less chance for collisions.
* **BLAKE** / **BLAKE2 **/ **BLAKE2s **/ **BLAKE2b** is a family of fast, secure cryptographic hash functions.
  * The **BLAKE2 **function is improved version of **BLAKE**.
  * **BLAKE **has **256-bit** variant \(BLAKE-256, BLAKE2s\) and **512-bit **variant \(BLAKE-512, BLAKE2b\).
  * The BLAKE2 hash function has similar security strength like SHA-256.

As of Mar 2018, **no collisions are known **for: **SHA256**, **SHA3-256**, **Keccak-256**, **BLAKE2s**, **RIPEMD160 **and few others

* **Brute forcing **to find collision costs: 2<sup>128</sup> for SHA256 / SHA3-256 and 2<sup>80</sup> for RIPEMD160.
* Respectively, on a powerful enough **quantum computer**, it will cost less time: 2<sup>256/3</sup> and 2<sup>160/3</sup> respectively. Still (as of Mar 2018) so powerful quantum computers are not known to exist.

Learn more about cryptographic hash functions, their strength and **attack resistance** at: [https://z.cash/technology/history-of-hash-function-attacks.html](https://z.cash/technology/history-of-hash-function-attacks.html)

