# Modern KDFs: Bcrypt, Scrypt and Argon2

Modern key-derivation functions (KDF) like **Scrypt** and **Argon2** derive a key (of fixed length) from a password (text) and are **resistant** to **dictionary attacks** and **ASIC attacks**.

Algorithms like **Bcrypt**, **Scrypt** and **Argon2** are considered **secure** KDF functions. They use **salt** + many **iterations** + a lot of **CPU** + a lot of **RAM** memory. This makes very hard to design a custom hardware to significantly speed up password cracking.

It takes **CPU time** to derive the key (e.g. 0.2 sec) + **memory** (RAM). The calculation process is memory-dependent, so **the memory access is the bottleneck**. 

Thus, **cracking passwords will be slow** and inefficient (e.g. 5-10 attempts / second), even on very good password cracking hardware. The goal is to make practically infeasible to perform a brute-force attack to guess the password from its hash.

Let's discuss in more details **Scrypt**, **Bcrypt** and **Argon2**.
