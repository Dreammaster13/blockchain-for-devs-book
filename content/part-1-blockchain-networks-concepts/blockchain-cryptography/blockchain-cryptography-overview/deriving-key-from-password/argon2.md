# Argon2: Derive Key from Password

**[Argon2](https://en.wikipedia.org/wiki/Argon2)** is modern **ASIC-resistant** and **GPU-resistant** key derivation function. It has better password cracking resistance than PBKDF2, Bcrypt and Scrypt (for similar configuration parameters).

It is considered that when configured correctly, **Argon2 is more secure** than Scrypt, Bcrypt and PBKDF2.

## Variants of Argon2

The **Argon2** function has several variants:

 - **Argon2d** – provides strong GPU resistance, but has potential side-channel attacks (possible in very special situations)
 - **Argon2i** – provides less GPU resistance, but has no side-channel attacks
 - **Argon2id** – recommended (combines the Argon2d and Argon2i)

## Config Parameters of Argon2

**Argon2** has the following **config parameters**, which are very similar to Scry:
 - **password** (P): the password (or message) to be hashed
 - **salt** (S): random-generated salt (16 bytes recommended for password hashing)
 - **iterations** (t): number of iterations to perform
 - **memorySizeKB** (m): amount of memory (in kilobytes) to use
 - **parallelism** (p): degree of parallelism (i.e. number of threads)
 - **outputKeyLength** (T): desired number of returned bytes

## Argon2 - Example

You can **play with the Argon2** password to key derivation function online here: http://antelle.net/argon2-browser.

![](/assets/Argon2-online.png)

## Argon2 Calculation in Python - Example

Now, we shall write some **code in Python** to derive a key from a password using the **Argon2** algorithm.

First, install the Python package `argon2_cffi` using the command:
```
pip install argon2_cffi
```

Now, write the Python code to calculate Argon2:
```python
import argon2

argon2Hasher = argon2.PasswordHasher(time_cost=50, memory_cost=102400, parallelism=8, hash_len=32, salt_len=16)
hash = argon2Hasher.hash("s3kr3tp4ssw0rd")
print("Derived key:", hash)
```

The **Argon2** calculation takes several **input configuration settings**: **time_cost** (number of iterations), **memory_cost** (memory to use in KB), **parallelism** (how many parallel threads to use), **hash_len** (the size of the derived key), **salt_len** (the size of the random generated salt).

Sample **output** from the above code execution:
```
Derived key: $argon2id$v=19$m=102400,t=50,p=8$JPoIjwAPeCGiLFwdhcCMwQ$Mf9d8TtMA7b21/8VTyW+zEYlzMo2TyPclkf4qnNUzCI
```

Note that the above output is not the derived key, but a **hash string** in a standardized format, which holds the Argon2 algorithm config **parameters** + the derived **key** + the random **salt**. By design, the salt and the derived key should be different at each code execution.

Try to change the **time_cost** or the **memory_cost** settings and see how they affect the **execution time** for the key derivation.