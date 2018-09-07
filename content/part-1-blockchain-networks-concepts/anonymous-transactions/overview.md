# Chapter 1.10. Anonymous Transactions

## CoinJoin, Ring Confidential Transactions, zkSNARKS, Zcash, Dash, PIVX, Monero, Verge, Bytecoin

# Table of Contents
- Anonymization models in cryptocurrencies
  - CoinJoin: Mixing Transactions to Increase Privacy
  - MimbleWimble
  - Zero-Knowledge Proofs and zk-SNARKs
  - Crypto_Note_
- Privacy Coins
  - Zcash, Dash, PIVX, Monero, Verge, Bytecoin
![](/assets/anonymous-transactions-table-of-contents-01.png)
![](/assets/anonymous-transactions-table-of-contents-02.png)


# **Anonymization Models on the Blockchain**
- **CoinJoin** transaction mixing
  - Mixing transactions to increase privacy
- **Zero-Knowledge** **Proofs**
  - Prove you know something, without revealing it
- **MimbleWimble** protocol
  - Guarantees strong privacy and confidentiality.
- **Crypto_Note_** 
  - Allows the creation of completely anonymous egalitarian cryptocurrencies
  - **Ring** **Signatures**+**Ring Confidential Transactions** + **Stealth Addresses**


# CoinJoin

```cs
Mixing Transactions to Increase Privacy
```

![](/assets/anonymous-transactions-coinjoin-01.png)


# CoinJoin Transaction Mixing
- Blockchain transactions can have **many inputs and outputs**
  - The only thing the network cares about is that they add up
- Instead of sending directly, **collude with other users to send a common transaction**
  - Everybody sees what they sign, so coins can’t be stolen
  - Use a **standard size for the outputs**, so it’s not obvious from which inputs they come
    - If needed, split big transaction in many standard-sized chunks
  - The users can meet through a centralized service, or through decentralized protocols
- Example: Blockchain Explorer  


# CoinJoin: Example of Transaction Joining
![](/assets/anonymous-transactions-coinjoin-example-of-transaction-joining-01.png)


# **MimbleWimble**

```cs
Scalability, Privacy and Fungibility
```

![](/assets/anonymous-transactions-mimblewimble-01.png)


# **MimbleWimble**
- **MimbleWimble** protocol – Proposed by **Tom Elvis Jedusor** 
- Scalling solution for Bitcoin
  - Guarantees strong privacy and confidentiality
- Uses **elliptic-curve cryptography**
- **No Transactions**
  - **Blocks**contains only **Input &rarr; Output**
- Big Number * G = ECC Point
- (Private Key) * (Point) = Public Key


# **MimbleWimble**
- Users have no unique public **addresses**
  - Using **blinding factor**, that **maintains** the **privacy**
- **Mining the Coin**
- **Sending Coins**
-   (113*G + 3*H)
-   ((113+28)*G + 3*H) - (113*G + 3*H) = 28*G + 0*H
<div class="fragment balloon" style="top:27.78%; left:87.25%; width:34.38%">Coins **Reward**</div>
<div class="fragment balloon" style="top:38.11%; left:10.85%; width:36.01%">Generating our **Blinding Factor**</div>
<div class="fragment balloon" style="top:53.54%; left:92.54%; width:47.60%">Previous **Owner** **equation**</div>
<div class="fragment balloon" style="top:53.73%; left:37.01%; width:44.96%">Receiver **Blinding Factor**</div>


# **MimbleWimble**
- **Possession of private keys**
  - **Proof** is not achieved by directly **signing** the **transaction**
- **Verification of zero sums**
  - The sum of outputs minus inputs always equals zero
  - Does not reveal the actual amounts
- **Balance**is based on **elliptic-curve cryptography**
  - **Pedersen Commitment**
- **Range proofs**
  - **Proof** that a number falls within a given range, without revealing it
- **More info:**github.com/mimblewimble/grin/blob/master/doc/intro.md


# Demo
- Hidden Amounts
![](/assets/anonymous-transactions-demo-01.png)


# Zero-Knowledge Proofs

```cs
Prove You Know Something,without Revealing It
```

![](/assets/anonymous-transactions-zero-knowledge-proofs-01.png)


# Zero-Knowledge Proof
- **Zero-knowledge proof**
  - A proof that a someone knows something, without revealing it
- **Interactive zero-knowledge proof**
  - **Prover** convinces a **verifier** that he knows a secret
  - Sequence of **interactions** (exchanged messages) between them
- **Non-interactive zero-knowledge proof**
  - No or little **interaction** between **prover** and **verifier** is needed


# Zero Knowledge Proofs
- **Completeness** – **prover** can convince the **verifier** about **any true statement**
- **Soundness** – prover **cannot** convince the verifier about a **false statement**
- **Zero-knowledgeness** – verifier doesn’t learn anything other than the fact that the statement is true
- **Privacy** – the transcript of the interactions is useless to a third party
- **Zero-knowledge** proofs can guarantee the validity of transactions
  - Without revealing what's inside the transactions


# Zero Knowledge Proofs Example

```cs
Interactive Demo
```

![](/assets/anonymous-transactions-zero-knowledge-proofs-example-01.png)


# Zero Knowledge Proofs Example
- **Graph three-coloring** problem
- It is hard to determine if a **solution** exists
- Very **large** and **complex graphs**take huge computing power to be solved
![](/assets/anonymous-transactions-zero-knowledge-proofs-example-01.png)


<!-- # Zero Knowledge Proofs Example -->
- Hiring a big **Google cloud** to solve it for us
- We don’t want to **pay** before actually knowing that it was solved
- **Google** doesn’t want to share the solution without getting **paid**
![](/assets/anonymous-transactions-zero-knowledge-proofs-example-2-01.png)


<!-- # Zero Knowledge Proofs Example -->
- **Google** covers the solution with hats (**encryption**)
- This protects the **solution**
- This doesn’t prove that **Google** has the **solution**
![](/assets/anonymous-transactions-zero-knowledge-proofs-example-3-01.png)


<!-- # Zero Knowledge Proofs Example -->
- **Google** lets me challenge the **solution**
- **Google** **reveals** small portion of the **solution**
- **Verifying** that the two vertices are **different** colors
![](/assets/anonymous-transactions-zero-knowledge-proofs-example-4-01.png)


<!-- # Zero Knowledge Proofs Example -->
- This process can be repeated while **randomizing** the **colors** each time
- **Repeating** it many times **decreases** the chance of **cheating**
- Why is this "**Zero Knowledge Proof**"
  - **Completeness:** if **Google** is telling the truth, then they will eventually convince me (at least with high probability).
  - **Soundness: Google** can only convince me if they’re actually telling the truth
  - **Zero- knowledgeness :** I don’t learn anything else about **Google’s** solution


<!-- # [Demo -->

```cs
Three Coloring Graph
```

![](/assets/anonymous-transactions-demo-01.png)


# Zero Knowledge Proofs in Blockchain
- Key Generator
- Proof
- Generator
- Verification
<div class="fragment balloon" style="top:40.38%; left:50.81%; width:34.38%">Toxic Waste</div>


# Zero Knowledge Proofs in Programming
- A **program** is **encoded** as a **mathematical equation**
  - Not all programs can be encoded – no loops or recursion allowed
  - If the equation **holds**, the program has been **executed correctly**
- Using a set of **related keys**, verifier asks the equation to be evaluated at some (encrypted) point **x**
  - With **homomorphic hiding**, the verifier can check that the equality in the equation holds without knowing the values
  - If equal – strongly suggests prover knows a secret value **w**
  - The keys are related through a parameter known as **“toxic waste”**
    - Has to be destroyed after the keys are generated, to avoid creating fake proofs


# Zero Knowledge Proofs in Blockchain
- The **program** in question can be the **transaction validation**machinery
- Proves that the **balances** have been **updated correctly**
  - Sum of outputs is less than or equal to sum of inputs
  - No negative-valued outputs
  - Sender had higher balance before the TX
  - Sender is in possession of needed private keys
- **Without** revealing the balances **or** participants


# Zero Knowledge Proof Protocols
- **Schnorr protocol**
  - Proof of knowledge of a discrete logarithm (works with ECC)
  - http://www.lsv.fr/Software/spore/schnorr.pdf
- **zk-SNARKs**
  - Zero-knowledge proof cryptosystem used in **Zcash**
  - **Z**ero-**K**nowledge **S**uccinct **N**on-Interactive **Ar**gument of **K**nowledge
  - Build around the elliptic-curve cryptography (ECC)
  - https://z.cash/technology/zksnarks.html


# Crypto_Note_

```cs
Allows the Creation of Completely Anonymous Egalitarian Cryptocurrencies
```

![](/assets/anonymous-transactions-crypto-note-01.png)


# Crypto_Note_
- **Crypto_Note_** is an open-source blockchain technology
  - Incorporates **privacy** by design: **untraceable payments**
  - CPU and GPU mineable **CryptoNight** proof-of-work algorithm
  - **https://cryptonote.org**
- Multiple cryptocurrencies are based on Crypto_Note_
  - Monero, Aeon, Bytecoin
  - Start your own Crypto_Note_ cryptocurrency: https://cryptonotestarter.org


# Crypto_Note_ Blockchain Analysis Resistance
- Mitigate risks associated with 
  - **Key re-usage**
  - **One-input-to-one-output tracing**
- Address for a payment 
  - **Unique one-time key**
  - Derived from the **sender's** and the **recipient's data**
- **Graph** without any cycles
  - Billions of possible graphs (**ring signature**produces ambiguity)
![](/assets/anonymous-transactions-crypto-note-blockchain-analysis-resistance-01.png)


# Video: Stealth Addresses
![](/assets/anonymous-transactions-video-stealth-addresses-01.png)


# **Stealth Addresses**
- **Stealth Addresses == one-time public key**
  - The key is **automaticly** **generated**
  - Being **recorded** as part of the **transaction**
- Privacy on coin transaction
- No link between the two addresses
- The sender has proof of the transfer existence
  - History of the transaction doesn’t exist


# Video: Ring Signatures
![](/assets/anonymous-transactions-video-ring-signatures-01.png)


# Ring Signatures: Untraceable Payments
- **Sender** **privacy**
  - Assured by using **Ring Signatures**
- **Actual Signer**+ **Decoy Signers**== **Ring Signature**
  - All members are equal and valid
- **Third parties**cannot verify witch output is being spent
- **Key Image**prevents double spending
  - **Cryptographic key** derived from the output being spent
  - Part of every **Ring Signature**transaction
  - One key per each output on the blockchain


# Video: Ring Confidential Transactions
![](/assets/anonymous-transactions-video-ring-confidential-transactions-01.png)


# Ring Confidential Transactions	
- **RingCT** – improvement of ring signature protocol hiding transaction amounts
  - Outputs are **no more**broken into **different rings**, because outside observers cannot see the amounts
- **Range Proofs**
  - **Proof** that a number falls within a given range, without revealing the number


# Standard Crypto_Note_ Transaction
![](/assets/anonymous-transactions-standard-crypto-note-transaction-01.png)


# Privacy Coins
- Zcash, Hush, Dash, PIVX, Monero, Verge, Bytecoin
![](/assets/anonymous-transactions-privacy-coins-01.png)


# Zcash
- How Zcash Works? 
![](/assets/anonymous-transactions-zcash-01.png)


# Zcash
- Open, permissionless blockchain
- Strong privacy protections
- Proof of work hash algorithm: **Equihash** 
- **Zero-knowledge** cryptography
- Selective transparency of transactions
- "**Shielded**" transactions hide 
  - Sender + Recipient + Value (see an example at Zchain Explorer)
- All transactions published on a public blockchain
- If **Bitcoin** is like **http** for money, **Zcash** is like **https**
![](/assets/anonymous-transactions-zcash-01.png)


# How Zcash Works?
- **Zcash** encrypts the contents of **shielded transactions**
- Payment information is **encrypted**
- Novel cryptographic method is used to verify their validity
- Transaction metadata is encrypted
- Uses **zk-SNARK** to prove that nobody is cheating or stealing
![](/assets/anonymous-transactions-how-zcash-works-01.png)


<!-- # How Zcash Works? -->
- Enables users to send public payments 
  - Similarly to Bitcoin
- Supports both **shielded** and **transparent** addresses
  - Send privately or publicly
- Payments 
  - Shielded address &rarr; transparent address reveal the received balance
  - Transparent address &rarr; shielded address protect the receiving value
![](/assets/anonymous-transactions-how-zcash-works-2-01.png)


# Building Blocks of a Transaction
- **Shielded address**
  - Addresses start with a **“z**”
  - Requires the generation of a**zero-knowledge proof**
- **Transparent addresses**
  - Addresses start with a **“t”**
  - Require interaction with “Transparent Value Pool” (TVP)
  - Transaction **fee** also passes through the **TVP**&rarr; always visible
![](/assets/anonymous-transactions-building-blocks-of-a-transaction-01.png)


# Sending Transactions Between Shielded and Transparent Addresses
- **ZEC** – cryptocurrency of Zcash
- Different set of properties depending on 
  - Address type
  - Previous address(es)
- Transparent address
  - Unspent balance &rarr; publicly **viewable**
- Balance being sent to transparent, shielded addresses or combination output ZEC from a transparent address &rarr; **visible**
- Sending transparent ZEC to a shielded address &rarr; **breaking the linkability** between future transparent addresses
![](/assets/anonymous-transactions-sending-transactions-between-shielded-and-transparent-addresses-01.png)


# Private Payment Channels
- **Blind Off-chain Lightweight Transactions (BOLT)**
- Fast, private payment channel protocol inspired by the **Lightning Network**
- No block confirmations
- Eliminates the linkage between payments within a channel
- Merchant know the channel he has opened and being paid 
- **Payment channel**(i.e. Lightning Network) 
  - Escrow funds & resolve disputes, not private
- Two protocols
  - Non-interactive
  - Interactive (**bidirectional** payments)
![](/assets/anonymous-transactions-private-payment-channels-01.png)


<!-- # [Demo -->
- Zcash Block Explorer
![](/assets/anonymous-transactions-demo-01.png)


# Dash
- How Dash Works? 
![](/assets/anonymous-transactions-dash-01.png)


# Dash
- **Instant**
- Send and confirm payments in lessthan a second
- **Private**
- Protect your financial information
- **Secure**
- Transactions confirmed by200 TH of X11 ASIC
![](/assets/anonymous-transactions-dash-01.png)
![](/assets/anonymous-transactions-dash-02.png)
![](/assets/anonymous-transactions-dash-03.png)


<!-- # Dash -->
- Fully-incentivized peer-to-peer network
- **Instant Send**(like a lightning network)
- **Private Send**(like Zcash shielded transactions)
- DAO with **decentralized governance**by blockchain (DGBB)
- Two-tier architecture:
  - **Miners** rewarded for **securing**and**writing transactions** to the chain 
    - Proof of work algorithm: **X11**
  - **Masternodes** 
    - Rewarded for **validating**, **storing** and **serving** the blockchain to users
    - Work in **quorums**


# What are Masternodes in Dash?
- **Masternode** == server connected to the network 
  - Guarantees a certain minimum level of performance and functionality to perform certain tasks related to **Private Send**and **Instant Send**
- Using **Proof of Service**(addition to the Proof of Work)
- Allowed to **vote** on governance and funding proposals
- Anyone can run a **masternode**
  - **Proof of ownership**of 1000 Dash
- Every 16,616 blocks (~ 28 days) а **superblock** is created
- Randomly selected for payment


<!-- # Dash – [Demo -->
![](/assets/anonymous-transactions-dash-demo-01.png)


# PiVX
- How PiVX Works? 
![](/assets/anonymous-transactions-pivx-01.png)


# PIVX
- Private Instant Verified Transaction **(PIVX)**
- Decentralized, open-source, privacy-oriented cryptocurrency 
- Launched as **Darknet** (DNET)
- Runs on the **Blackcoin PoS 2.0**protocol
- Based on a Bitcoin fork
- 100% Proof of Stake
- **Masternodes** verify transactions
- **90%** of rewards go to **Masternodes** and **Proof of Stake nodes**
- **10%** going to community projects
![](/assets/anonymous-transactions-pivx-01.png)


<!-- # PIVX – [Demo -->
- http://www.presstab.pw/phpexplorer/PIVX/
![](/assets/anonymous-transactions-pivx-demo-01.png)


# Monero
- How Does Monero Work?
![](/assets/anonymous-transactions-monero-01.png)


# Monero
- **Secure**
- **Private**
- Immutably recorded
- Ring signatures
- and confidential transactions
![](/assets/anonymous-transactions-monero-01.png)
![](/assets/anonymous-transactions-monero-02.png)


<!-- # Monero -->
- **Untraceable**
- **Fungible**
- Units of Monerocannot be blacklistedby vendors
- Transactions cannotbe linked to a particular user
![](/assets/anonymous-transactions-monero-2-01.png)
![](/assets/anonymous-transactions-monero-2-02.png)


# How Does Monero Work?
- Ring Signatures
- RingCT
- Stealth Addresses
![](/assets/anonymous-transactions-how-does-monero-work-01.png)


# Monero in a Nutshell
- PoW algorithm: **CryptoNight**
- No one can tell how rich you are
- **Unlinkability** – one-time address not linked to public address
- **Receiving address**== randomly created brand new one-time destination address (on send transaction)
- Public record does not contain any mention that funds were received 
- **Public address**never appears in the public record of transactions
- **“Stealth address”**recorded and only the recipient, can recognize the incoming funds
- **Secret view key** is used to check each transaction by recipient


<!-- # Monero in a Nutshell -->
- Ring signatures enable **“transaction mixing”**to occur
- **Transaction mixing** – obfuscation technique to make tracing very hard job
- No one can tell which of the funds were really the source of the transaction
- **“Mixin” level**
-  Larger mixin level == larger size of the transaction 


<!-- # [Demo -->
- Monero Block Explorer and Stats
![](/assets/anonymous-transactions-demo-01.png)


<!-- # [Demo -->
- Monero (Cryptonote) Address Generation
![](/assets/anonymous-transactions-demo-01.png)


<!-- # [Demo -->
- Monero Active Nodes Distribution
![](/assets/anonymous-transactions-demo-01.png)


# Verge
- How Does Verge Work? 
![](/assets/anonymous-transactions-verge-01.png)


# Verge
- Privacy cryptocurrency 
- Focused on communication through protocols like **I2P** and **Tor**
- 5 Proof-of-Work algorithms
  - **Scrypt**, **X17**, **Lyra2rev2**, **myr-groestl**, **blake2s**
  - This was probably not a good idea
- Algorithms have a **30-second target block time**
- Difficulty influenced by the algorithms **hash rate**
- **P2P** transaction support for **Telegram** and **Discord**
- Future development to incorporate **Rootstock** (RSK)
![](/assets/anonymous-transactions-verge-01.png)


# Bytecoin
- How Does Bytecoin Work? 
![](/assets/anonymous-transactions-bytecoin-01.png)


# Bytecoin
- The first untraceable cryptocurrency with the **Crypto_Note_** technology
- Instant private transactions
- Totally untraceable
- No additional fees
- Limited to **184.47** billion BCN
- **Modular code base**
  - Build application with source code modules
- **Powerful and flexible API**
  - Multi-purpose and multi-layer
- **Multisignature**
![](/assets/anonymous-transactions-bytecoin-01.png)


# Summary
- **CoinJoin**,**Zero-Knowledge Proof**, **MimbleWimble**,**Crypto_Note_**
- **Zcash** – open, permissionless using zero knowledge cryptography
- **Private Payment Channels**– blind off-chain lightweight transactions
- **Dash** – unique fully-incentivized peer-to-peer network
  - **Masternodes** – server connected to the network 
- **PIVX** – private instant verified transaction
- **Monero** – secure private untraceable currency
  - **Ring Signatures & RingCT & Stealth Addresses**
- **Verge** – has **5 Proof-of-Work**algorithms
- **Bytecoin** – using **Crypto_Note_** technology
![](/assets/anonymous-transactions-summary-01.png)


# Resources
- zk-SNARKs: https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/ , https://medium.com/@VitalikButerin/zk-snarks-under-the-hood-b33151a013f6 
- Zcash: https://z.cash/ 
- How Zcash Works: https://z.cash/technology/ 
- Building a Block of a Transaction: https://z.cash/blog/anatomy-of-zcash.html 
- Dash: https://dashpay.atlassian.net/wiki/spaces/DOC/pages/29360130/Introducing+Dash 
- Masternodes: https://dashpay.atlassian.net/wiki/spaces/DOC/pages/1146943/Masternodes 
- Privacy coins: https://coincentral.com/privacy-coins-what-are-they-how-do-they-work-and-why-are-they-needed/
- Monero: https://getmonero.org/ 
- Crypto_Note_: https://cryptonote.org/inside/ 
- Privacy coins: https://coincentral.com/privacy-coins-what-are-they-how-do-they-work-and-why-are-they-needed/
- Bytecoin: https://wiki.bytecoin.org/wiki/Main_Page 




