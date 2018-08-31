# The Diffie-Hellman Key Exchange (DHKE) Protocol

Now, let's explain how the DHKE works.

## The Math behind DHKE

It is based on a simple property of **modular exponentiations**:

(g<sup>a</sup>)<sup>b</sup> mod p = (g<sup>b</sup>)<sup>a</sup> mod p

where **g**, **a**, **b** and **p** are positive integers. Thus, if we have **g<sup>a</sup>** mod **p** and **g<sup>b</sup>** mod **p**, we can calculate **g<sup>ab</sup>** mod **p**, without revealing **a** or **b** (which are called **secret exponents**).

In math, these is no efficient algorithm which can find a secret exponent. If we have **m**, **g** and **p** from the below equation:

m = g<sup>s</sup> mod p

there is not efficient (fast) algorithm to find the secret modular exponent **s**.

## The DHKE Protocol

Now, after we are familiar with the above mathematical properties of the modular exponentiations, we are ready to explain **the DHKE protocol**. This is how it works:

![](/assets/Diffie-Hellman-Key-Exchange-Protocol.png)

Let's explain each step of this key-exchange process:

 - Alice and Bob agree to use tow public integers: **modulus p** and **base g**.
   - For example, let **p** = 23 and **g** = 5.
   - The integers **g** and **p** are public, typically hard-coded constants in the source code.
   
 - Alice chooses a **secret integer a** (e.g. **a** = 4), then calculates and sends to Bob the number **A = g<sup>a</sup> mod p**.
   - The number **A** is public. It is sent over the public channel and its interception cannot reveal the secret exponent **a**.
   - In our case we have: **A** = 5<sup>4</sup> mod 23 = 4.

 - Bob chooses a **secret integer b** (e.g. **b** = 3), then calculates and sends to Alice the number **B = g<sup>b</sup> mod p**.
   - In our case we have: **B** = 5<sup>3</sup> mod 23 = 10

 - Alice computes s = B<sup>a</sup> mod p
   - In our example: **s** = 10<sup>4</sup> mod 23 = **18**

 - Bob computes s = A<sup>b</sup> mod p
   - In our example: **s** = 4<sup>3</sup> mod 23 = **18**

 - Alice and Bob now share a **secret number s**
   - **s** = A<sup>b</sup> mod p = B<sup>a</sup> mod p = (g<sup>a</sup>)<sup>b</sup> mod p = (g<sup>b</sup>)<sup>a</sup> mod p = g<sup>ab</sup> mod p = **18**
   - The shared secret key **s** cannot be computed from the publicly available numbers **A** and **B**, because the secret exponents **a** and **b** cannot be efficiently calculated.

This is how DHKE works. It exchanges a **non-secret sequence of integer numbers** over insecure, public (sniffable) channel (such as signal going through a cable or propagated by waves in the air), but does not reveal the secretly-exchanged shared private key.

Again, be warned that DHKE protocol is **vulnerable to man-in-the-middle attacks** where a hacker can intercept and modify the messages exchanged between the parties.

