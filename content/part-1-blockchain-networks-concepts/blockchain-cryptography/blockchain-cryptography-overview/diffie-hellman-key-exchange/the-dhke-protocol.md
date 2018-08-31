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

Now, after we are familiar with the above properties of the modular exponentiations, we are ready to explain the DHKE protocol. This is how it works:

Alice and Bob agree to use a modulus p = 23 and base g = 5 

Alice chooses a secret integer a = 4, then sends Bob A = ga mod p
A = 54 mod 23 = 4

Bob chooses a secret integer b = 3, then sends Alice B = gb mod p
B = 53 mod 23 = 10

Alice computes s = Ba mod p
s = 104 mod 23 = 18

Bob computes s = Ab mod p
s = 43 mod 23 = 18

Alice and Bob now share a secret number s
s = (ga)b mod p = (gb)a mod p
s = 18

s cannot be computed from A and B



