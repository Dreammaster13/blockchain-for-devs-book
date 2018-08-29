# Deriving a Key from Password: Key Derivation Functions (KDF)

In this section we shall explain in details how to securely derive a key from a password and the most popular **key derivation functions** (**KDFs**) used in practice: [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2), [Bcrypt](https://en.wikipedia.org/wiki/Bcrypt), [Scrypt](https://en.wikipedia.org/wiki/Scrypt) and [Argon2](https://en.wikipedia.org/wiki/Argon2).

<div class="video-player">
  Watch the video: <a target="_blank" href="https://www.youtube.com/watch?v=hUuld46yqOU">https://www.youtube.com/watch?v=hUuld46yqOU</a>.
</div>
<script src="/assets/js/video.js"></script>

We shall discuss the strong and weak sides of the above mentioned KDFs and when to use them.

## Key Derivation Functions - Concepts

In cryptography we often use **passwords** instead of **binary keys**, because passwords are easier to remember, to write down and can be shorter.

When a certain algorithms needs a **key** (e.g. for encryption or for digital signing) a **key derivation function** (password -> key) is needed.

We already noted that using `SHA-256(password)` as key-derivation is insecure! It is vulnerable to many attacks: **brute-forcing**, **dictionary attacks**, **rainbow attacks** and others, which may reverse the hash in practice and attacker can obtain the password.

## Modern Key Derivation Functions

[PBKDF2](https://en.wikipedia.org/wiki/PBKDF2), [Bcrypt](https://en.wikipedia.org/wiki/Bcrypt), [Scrypt](https://en.wikipedia.org/wiki/Scrypt) and [Argon2](https://en.wikipedia.org/wiki/Argon2) are significantly stronger key derivation functions and are designed to survive password guessing attacks.
 
By design **secure key derivation functions** use **salt** (random number, which is different for each key derivation) + **many iterations** (to speed-down eventual password guessing process).

To calculate a secure KDF it takes some **CPU time** to derive the key (e.g. 0.2 sec) + some **memory (RAM)**. Thus deriving the key is "computationally expensive", so password cracking will also be computationally expensive.

When a modern KDF function is used with appropriate config parameters, **cracking passwords** will be **slow** (e.g. 5-10 attempts per second, instead of thousands or millions attempts per second).

Let's learn more about these modern KDF.