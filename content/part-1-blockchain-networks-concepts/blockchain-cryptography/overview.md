# Chapter 1.2. Blockchain Cryptography: Elliptic Curves, Hashes, Keys, Blockchain Addresses, Encryption, Key Derivation, Wallets

In this chapter we will introduce the **cryptography concepts** used in the blockchain networks, hashes, elliptic curves, public and private keys, encryption, the cryptography behind wallets and transactions.

We shall start by major cryptography concepts like hashing and cryptographic **hash functions**, **HMAC** and **key derivation** algorithms, symmetric and asymmetric **encryption algorithms**, **secure random generators** and pseudo-random generator functions (PRNG).

After the first few concepts, we shall write some code to play with them. We shall implement **calculation of hashes**, **HMAC calculations** by text and key, password to key derivation using **Scrypt** and **AES**-based **symmetric key encryption** and **decryption**.

The core of this lesson will be devoted to **elliptic curve cryptography** (ECC) and the crypto-systems used in the most popular blockchain networks like **Bitcoin** and **Ethereum**. We shall explore deeply the **ECDSA** and **EdDSA** digital signatures using the `secp256k1` and `Curves25519` elliptic curves.

