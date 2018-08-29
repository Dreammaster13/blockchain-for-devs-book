# BCrypt: Derive Key from Password

**[Bcrypt](https://en.wikipedia.org/wiki/Bcrypt)** is another cryptographic KDF function, **older than Scrypt**, and is **less resistant **to ASIC and GPU attacks. It provides configurable iterations count, but uses constant memory, so it is easier to build hardware-accelerated password crackers.

Modern applications should **prefer Scrypt** instead of Bcrypt.