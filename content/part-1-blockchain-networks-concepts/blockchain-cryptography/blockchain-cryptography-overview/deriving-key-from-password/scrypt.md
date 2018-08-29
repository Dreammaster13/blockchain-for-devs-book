# Scrypt: Derive Key from Password

**Scrypt** ([RFC 7914](https://tools.ietf.org/html/rfc7914.html)) is a strong cryptographic key-derivation function. It is memory-intensive, designed to prevent **GPU**, **ASIC** and **FPGA** attacks (highly efficient password cracking hardware).

The Scrypt algorithms takes several **input parameters**:
```
key = Scrypt(password, salt, N, r, p, derived-key-len)
```

## Scrypt Parameters

The **Scrypt parameters** are:
 - `N` – iterations count (affects memory and CPU usage), e.g. 16384
 - `r` – block size (affects memory and CPU usage), e.g. 8
 - `p` – parallelism factor (threads to run in parallel - affects the memory, CPU usage), usually 1
 - `password`, `salt` and `derived-key-length` - work like in the others KDF algorithms

The **memory** in Scrypt is accessed in strongly **dependent order** at each step, so the memory access speed is the algorithm's bottleneck. The memory required is calculated as follows:
```
Memory used = 128 * N * r * p bytes
```
Example: e.g. 128 \* N \* r \* p = 128 \* 16384 \* 8 \* 1 = 16 MB

**Choosing parameters** depends on how much you want to wait and what level of security (password cracking resistance) do you need:
 - Sample parameters for **interactive login**: N=16384, r=8, p=1 (RAM = 16MB)
 - Sample parameters for **file encryption**: N=1048576, r=8, p=1 (RAM = 1GB)

You can perform tests and choose the Scrypt parameters yourself. In **MyEtherWallet**, the default parameters are  N=8192, r=8, p=1 (which is not strong enough for crypto wallet, but this is how it works).

## Scrypt - Example

You can play with **Scrypt** key derivation online here: https://8gwifi.org/scrypt.jsp.

![](/assets/Scrypt-key-derivation.png)

## Scrypt Calculation in Python - Example

Now, we shall write some **code in Python** to derive a key from a password using the Scrypt algorithm.

First, install the Python package `scrypt` using the command:
```
pip install scrypt
```

Now, write the Python code to calculate Scrypt:
```python
import scrypt, binascii

salt = binascii.unhexlify('df1f2d3f4d77ac66e9c5a6c3d8f921b6')
passwd = "p@$Sw0rD~3".encode("utf8")
key = scrypt.hash(passwd, salt, 16384, 8, 1, 32)
print("Derived key:", binascii.hexlify(key))
```

The **Scrypt** calculation function takes several **input parameters**: the **password** (bytes sequence), the **salt** (bytes sequence), **iterations** count, **block size** for each iteration, **parallelism** factor and the output **key length** (number of bytes for the derived key).

Try to change the number of **iterations** or the **block size** and see how it affects the **execution time**.