# Diffie–Hellman Key Exchange (DHKE) - Concepts

**Diffie–Hellman Key Exchange** (DHKE) is a cryptographic method (protocol) to **securely exchanging cryptographic keys** over a public (insecure) channel. Once the keys are securely exchanges, an encrypted communication can start, e.g. using a symmetric cipher like AES.

DHKE was one of the first **public-key protocols**, which allows two parties to exchange data securely, so that is someone sniffs the communication between the parties, the information exchanged can be revealed.

The Diffie–Hellman (DH) method allows two parties that have no prior knowledge of each other to jointly establish a **shared secret key over an insecure channel**.

Note that the DHKE method is **resistant to [sniffing attacks](https://en.wikipedia.org/wiki/Sniffing_attack)** (data interception), but it is vulnerable on **[man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)** (attacker secretly relays and possibly **alters the communication** between two parties).
