# Chapter 1.2. Blockchain Cryptography: Hashes, Elliptic Curves, Keys, Blockchain Addresses, Encryption, Key Derivation, Crypto Wallets

In this chapter we will introduce the **cryptography concepts** used in the blockchain networks, hashes, elliptic curves, public and private keys, encryption, the cryptography behind wallets and transactions.

<div class="video-player">
  Watch the video: <a target="_blank" href="https://youtu.be/QbKJfQgQaU4">https://youtu.be/QbKJfQgQaU4</a>.
</div>
<script src="/assets/js/video.js"></script>

We shall start by major cryptography concepts like hashing and cryptographic **hash functions**, **HMAC** and **key derivation** algorithms, symmetric and asymmetric **encryption algorithms**, **secure random generators** and pseudo-random generator functions \(PRNG\).

After introducing the first few crypto concepts, we shall write some code to play with them. We shall implement **calculation of hashes**, **HMAC calculations** by text and key, password to key derivation using **Scrypt** and **AES**-based **symmetric key encryption** and **decryption** with HMAC for message integrity.

The core of this lesson will be devoted to practical **elliptic curve cryptography** \(ECC\) and the crypto-systems used in the most popular blockchain networks like **Bitcoin** and **Ethereum**. We shall explore deeply the **ECDSA** and **EdDSA** digital signatures schemes using the `secp256k1` and `Curve25519` elliptic curves and shall explain how **blockchain addresses** are calculated and how **digital signatures** are created and verified in the Ethereum blockchain.

Next, we shall explain the cryptography behind the **crypto wallets**, the concept of **hierarchical \(HD\) wallets**, the BIP39 and BIP44 standards, the seed words and hierarchical key derivation.

A few words will be devoted to **quantum-safe cryptography** and which classical crypto algorithms are quantum-safe \(like hashes and symmetric key ciphers\) and which are **quantum-broken** \(like most digital signature schemes and ECDSA\).

![](/assets/blockchain-cryptography.jpg)

After the next portion of concepts, we shall **write some code**: play with Ethereum message signing and signatures verification, generating private keys, deriving public keys and addresses for the Ethereum and Bitcoin networks, as well as implementing RSA-based asymmetric encryption.

Finally, we shall explore popular **crypto libraries** for implementing blockchain crypto algorithms for **JavaScript**, **Python**, **C\#** and **Java**, along with practical exercises to sign Ethereum JSON messages, generate ECC private keys and derive blockchain addresses and signing / verifying transactions in JS, Python, C\# and Java.

