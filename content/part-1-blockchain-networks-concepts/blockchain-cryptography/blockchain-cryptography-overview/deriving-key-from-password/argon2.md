# Argon2: Derive Key from Password

**[Argon2](https://en.wikipedia.org/wiki/Argon2)** is modern **ASIC-resistant** and **GPU-resistant** key-derivation function. It has better password cracking resistance than PBKDF2, Bcrypt and Scrypt (for similar configuration parameters).

It is considered that when configured correctly, **Argon2 is more secure** than Scrypt, Bcrypt and PBKDF2.


Argon2d – strong GPU resistance, potential side-channel attacks
Argon2i – less GPU resistance, no side-channel attacks
Argon2id – recommended (combines the Argon2d and Argon2i)
