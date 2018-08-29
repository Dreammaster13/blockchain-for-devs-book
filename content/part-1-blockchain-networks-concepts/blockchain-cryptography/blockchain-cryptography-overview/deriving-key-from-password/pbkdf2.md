# PBKDF2: Derive Key from Password

**PBKDF2** is a simple cryptographic key derivation function, which is resistant to [dictionary attacks](https://en.wikipedia.org/wiki/Dictionary_attack) and [rainbow table attacks](https://en.wikipedia.org/wiki/Rainbow_table) . It is based on iteratively deriving **HMAC** many times with some padding. It is described in the Internet standard [RFC 2898 (PKCS #5)](http://ietf.org/rfc/rfc2898.txt).

Technically, the **input data** for **PBKDF2** consists of:
 - `password` – array of bytes / string, e.g. "_p@$$w0rD~3_"
 - `salt` – securely-generated random bytes, e.g. "_dfc66e9c5…1b63_"
 - `iterations-count`, e.g. 1024 iterations
 - hash-function for calculating **HMAC**, e.g. `SHA256`
 - `derived-key-len` for the output, e.g. 256 bits

The **output data** is the **derived key** (e.g. 256 bits).

## PBKDF2 and Number of Iterations

**PBKDF2** allows to configure the number of **iterations** and thus to configure the time required to derive the key.
 - **Slower key derivation** means high login time / slower decryption / etc. and **higher resistance** to password cracking attacks.
 - **Faster key derivation** means short login time / faster decryption / etc. and **lower resistance** to password cracking attacks.
 - PBKDF2 is **not resistant** to [GPU attacks](https://security.stackexchange.com/questions/118147/how-are-gpus-used-in-brute-force-attacks) (parallel password cracking using video cards) and to [ASIC attacks](https://en.wikipedia.org/wiki/Custom_hardware_attack) (specialized password cracking hardware). This is the main motivation behind more modern KDF functions.
 
## PBKDF2 - Example
 
Try PBKDF2 key derivation online here: https://asecuritysite.com/encryption/PBKDF2z.

![](/assets/PBKDF2-calculator.png)

Try to **increase the iterations count** to see how this affects the speed of key derivation.

## PBKDF2 Calculation in Python - Example

Now, we shall write some **code in Python** to derive a key from a password using the PBKDF2 algorithm.

First, install the Python package `backports.pbkdf2` using the command:
```
pip install backports.pbkdf2
```

Now, write the Python code to calculate PBKDF2:
```python
import os, binascii
from backports.pbkdf2 import pbkdf2_hmac

salt = os.urandom(32)
passwd = "p@$$w0rD~3".encode("utf8")
key = pbkdf2_hmac("sha256", passwd, salt, 500000, 32)
print("Derived key:", binascii.hexlify(key))
```
