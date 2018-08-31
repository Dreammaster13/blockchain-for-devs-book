# Key Exchange by Mixing Colors

The Diffie–Hellman Key Exchange protocol is very similar to the concept of "**key exchanging by mixing colors**", which has a good visual representation, which simplifies its understanding. This is why we shall first explain how to exchange a secret color by **color mixing**.

The design of color mixing key exchange scheme assumes that if we have two liquids of different colors, we can **easily mix the colors** and obtain a new color, but the reverse operation is almost impossible: **no way to separate the mixed colors** back to their original color components.

This is the color exchange **scenario**, step by step:

 - **Alice** and **Bob**, agree on an arbitrary **starting (shared) color** that does not need to be kept secret (e.g. _yellow_).
 - **Alice** and **Bob** separately select a **secret color** that they keep to themselves (e.g. _red_ and _sea green_).
 - Finally **Alice** and **Bob** **mix** their secret color together with their mutually shared color. The obtained mixed colors area ready for public exchange (in our case _orange_ and _light sky blue_).

![](/assets/key-exchange-by-color-mixing-part-1.png)

The next steps in the color exchanging scenario are as follows:

- **Alice** and **Bob** publicly **exchange** the two **mixed colors**.
  - We assume that there is no efficient way to extract (separate) the secret color from the mixed color, so third parties cannot reveal the secret colors.
- Finally, **Alice** and **Bob** mix together the color they received from the partner with their own secret color.
  - The result is the **final color mixture** (_yellow-brown_) that is identical to the partner's color mixture.
  - It is the **securely exchanged shared key**.

![](/assets/key-exchange-by-color-mixing-part-2.png)

If a third party has intercepted the color exchange, it would be computationally difficult for them to determine the secret colors.

The **Diffie-Hellman Key Exchange** protocol is based on similar concept, but uses **discrete logarithms** and **modular exponentiations** instead of color mixing.
