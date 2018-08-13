# What is Cryptography and How It is Related to Blockchain?

**Cryptography **is the science of providing **security **and **protection **of information. It is widely used in blockchain systems to sign transactions, securely transfer blockchain assets, encrypt wallets and in many other scenarios.

Cryptography deals with **storing and transmitting data in a secure way**, such that only those, for whom it is intended, can read and process it. This may involve **encrypting and decrypting data** using symmetric or asymmetric encryption schemes \(like AES and RSA\), where one or more **keys** are used to transform data from plain to encrypted form and back. **Symmetric encryption** uses the same key to encrypt and decrypt messages, while **asymmetric encryption** uses a key pair \(encryption key and corresponding decryption key\). In blockchain encryption is used in wallets to protect the private keys and user's assets on the chain from unauthorized access.

Cryptography deals with **keys** \(large secret numbers\) and in many scenarios these **keys are derived **from numbers, passwords or passphrases using **key derivation algorithms** \(like PBKDF2 and Scrypt\). Wallets in the blockchain systems hold the user's keys, usually protected by a password or PIN code and sign transactions.

Cryptography defines **key-exchange algorithms** \(like Diffie-Hellman key exchange\), used to securely exchange data encryption **keys **between two parties that intend to transmit messages securely using **encryption**.

Cryptography uses **random numbers** and deals with **entropy** and secure generation of random numbers. Crypto wallets generate random keys to create a new blockchain account.

Cryptography provides **data hashing** functions \(like SHA-256, SHA3-256 and RIPEMD-160\), which transform messages to **message digest** \(hash of fixed length\), which cannot be reversed back to the original message and almost uniquely identifies it. In blockchain hashes are used for generating blockchain addresses, transaction identification and in many other algorithms and protocols.

Cryptography provides means of **digital signing of messages** which guarantee message authenticity, integrity and non-repudiation. Most digital signature algorithms \(like DSA, ECDSA and EdDSA\) use **asymmetric key pair** \(private and public key\): the message is **signed** by the private key and the signature is **verified** by the corresponding public key. In the blockchain systems **digital signatures **are used to sign transactions and allow users to transfer a blockchain asset from one address to another.

**Cryptography in the blockchain** networks deals also with **crypto wallets**, hierarchical key derivation, blockchain addresses, merkle trees, proof-of-work mining, and many other blockchain-specific crypto algorithms, standards and protocols. Blockchain developers need to understand cryptography very well in order to deal with wallets, keys, addresses, hashes, transactions, signatures, mining, etc. and to ensure strong level of security in the apps they build.

