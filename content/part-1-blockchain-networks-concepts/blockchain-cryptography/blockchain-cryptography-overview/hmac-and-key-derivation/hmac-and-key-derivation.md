# HMAC and Key Derivation

Simply calculating ```hash_func(key + msg)``` is considered **insecure** (see the [details](https://en.wikipedia.org/wiki/HMAC#Design_principles)).

It is recommended to use a **secure HMAC algorithm instead**, e.g. `HMAC-SHA256` or `HMAC-SHA3-512`.

## What is HMAC?

**HMAC** = **H**ash-based **M**essage **A**uthentication **C**ode (MAC code, calculated using a cryptographic hash function):
```
HMAC(key, msg, hash_func) -> hash
```
The results MAC code is a **message hash** mixed with a secret key. It has the cryptographic properties of hashes: **irreversible**, **collision resistant**, etc.

HMAC is used for message **authenticity**, message **integrity** and sometimes for **key derivation**

## Key Derivation Functions (KDF)

**Key derivation function** (KDF) is a function which transforms a variable-length password to fixed-length key (sequence of bits):
```
function(password) -> key
```
As **very simple KDF function**, we can use SHA256: just hash the password. Don't do this, because it is **insecure**. Simple hashes are vulnerable to **dictionary attacks**.

As more complicated function, you can derive a password by calculating **HMAC(salt, msg, SAH256)**, using some random value called "**salt**", which is stored along with the derived key and used later to derive the same key again from the password.

Using **HKDF (HMAC-based key derivation)** for key derivation is ** less secure** than modern KDFs, so experts recommend using stronger key derivation functions like [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2), [Bcrypt](https://en.wikipedia.org/wiki/Bcrypt), [Scrypt](https://en.wikipedia.org/wiki/Scrypt) and [Argon2](https://en.wikipedia.org/wiki/Argon2).
