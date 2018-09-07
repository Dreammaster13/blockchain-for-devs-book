# Blockchain Network Security - Overview, Threats, Attacks

## Blockchain Network Security, Wallet Security, Cold Wallets, The DAO Hack, Parity Hacks

# Table of Contents
- Vectors of Attack
- Blockchain Network &Consensus Security
- Client Side Security &Wallet Security
- Famous BlockchainDisasters
![](/assets/blockchain-security-table-of-contents-01.png)
![](/assets/blockchain-security-table-of-contents-02.png)
![](/assets/blockchain-security-table-of-contents-03.png)


# Vectors of Attack
- Cryptography, Blockchain Networks, Consensus, Wallets, Scam, Smart Contracts
![](/assets/blockchain-security-vectors-of-attack-01.png)


# **Attack the Cryptography**
- ECDSA attacks
  - Reused / unsafe random in signatures
- Random generator attacks
- **Collision attacks** (hash function attacks)
  - Birthday Attack
- Side-channel attacks
  - E.g. analyze the CPU power consumption
- Brute force attack **(BFA)** to find a key
- Quantum computing attacks
  - ECDSA is not quantum-resistant!
![](/assets/blockchain-security-attack-the-cryptography-01.png)
![](/assets/blockchain-security-attack-the-cryptography-02.png)


# **Attack the Blockchain Network**
- Networking attacks
  - Eclipse attacks / Sybil attacks
    - 13 ISPs hold 30% of Bitcoin 
    - 3 ISPs route 60% of all transactions
  - Denial of Service **(DoS)**attacks
- Consensus algorithm attacks
  - 51% attack &rarr; double-spending
- Transaction replay attack
![](/assets/blockchain-security-attack-the-blockchain-network-01.png)
![](/assets/blockchain-security-attack-the-blockchain-network-02.png)


# Attack the Wallets
- Malware (trojan horses / viruses / backdoors / keyloggers)
  - Can steal wallet private keys
- Scam / phishing site / fake app
  - Can steal wallet private keys
- Lost key &rarr; locked funds
- Attacking the **wallet backups**
- 3rd party hack, e.g. a site / app / library
- Server machine hack, e.g. the Coincheck exchange
![](/assets/blockchain-security-attack-the-wallets-01.png)


# Phishing Site Example: Electrum Wallet
![](/assets/blockchain-security-phishing-site-example-electrum-wallet-01.png)
![](/assets/blockchain-security-phishing-site-example-electrum-wallet-02.png)


# Phishing Site Example: Fake Electrum Wallet
![](/assets/blockchain-security-phishing-site-example-fake-electrum-wallet-01.png)
![](/assets/blockchain-security-phishing-site-example-fake-electrum-wallet-02.png)
![](/assets/blockchain-security-phishing-site-example-fake-electrum-wallet-03.png)


# Blockchain Network Security
- Security by Blocks, Chaining and Cryptography
![](/assets/blockchain-security-blockchain-network-security-01.png)


# Security by the Blocks
- **Blockchain**
  - Chain of digital **“blocks”** holding records of signed transactions
  - Each block connected to **blocks before and after**
  - Difficult to tamper
- Secured through **cryptography**
  - Transactions are **signed**
  - If something is altered &rarr; the signature will become invalid
![](/assets/blockchain-security-security-by-the-blocks-01.png)


<!-- # Security by the Blocks -->
- Decentralized and distributed across **peer-to-peer networks**
  - Continually **updated**
  - Kept in **sync**between all nodes
- Don’t have a **single point of failure**
  - Cannot be changed from a single computer
- Require massive amounts of computing power
  - **51% attack**
![](/assets/blockchain-security-security-by-the-blocks-2-01.png)


# Public and Private Blockchains
- **Public**(permissionless) 
  - Use computers connected to the **public Internet**
  - Any computer on the internet can join the network
  - Not good choice for enterprises
  - Designed around the principle of **anonymity**
  - Transactions are verified through **“mining”**
- **Private**(permissioned)
  - Only permits known organizations to join
  - They form a private, members-only **“business network”**
  - Use identity to **confirm membership**and **access privileges**
  - Transactions are verified through **“selective endorsement”**


# Public and Private Blockchains: Security
- **Public**(permissionless) 
  - 51% attack
    - &rarr; revert transactions
    - &rarr; double spending
  - Sybil attack
  - Denial of Service (DoS) attack / DDoS / spam transactions
  - Network difficulty manipulation attack
- **Private**(permissioned)
  - Join **unauthorized member**, e.g. though hacked server's credentials
  - Send **unauthorized**/ fake **transaction**, e.g. using hacked user
  - Unauthorized data access / leak of confidential data
  - Consensus algorithm atttacks


# Uses of Blockchain to Enforce Security
- The protection of **sensitive records**and **authentication** of the identity
- Enhancing structural security of **IoT devices**
- **Securing** internal communications
- Privacy and security of **digital chats**
- Increase security on three fronts:
  - Prevention of **identity theft**
  - Protection against **data tampering**
  - Protection of **critical infrastructure**
![](/assets/blockchain-security-uses-of-blockchain-to-enforce-security-01.png)


# Client-Side Security
- Cold Wallets, Exchanges, Threats
![](/assets/blockchain-security-client-side-security-01.png)


# Different Level of Security
- Level of Security depends on:
  - Type of wallet
  - Method of Authentication Used
  - User’s behavior
- Security issues:
  - Server-side stored private and public keys
  - Prone to hacker attacks
  - Exposition to counterparty risks
![](/assets/blockchain-security-different-level-of-security-01.png)


# Mobile Wallets
- Relatively high risk of information being lost or stolen
- Security may be increased through:
  - Screen lock
  - Applock 
  - Phone encryption
  - Phone passwords /**PIN codes**
![](/assets/blockchain-security-mobile-wallets-01.png)


# Desktop Wallets
- Security depends on behavior of account owner
- Visiting untrusted web resources 
- Having a designated device solely for the use of the wallet greatly increases its security
![](/assets/blockchain-security-desktop-wallets-01.png)


<!-- # Offline Wallets (Cold Walle -->
- Paper wallet
- Hardware wallet
- Relatively high security
- Stored offline
- No other connections
- Greatly reduces the risk
![](/assets/blockchain-security-offline-wallets-cold-wallets-01.png)
![](/assets/blockchain-security-offline-wallets-cold-wallets-02.png)


# General Wallet Security
- **Verify your email**
- **Two-step verification**
- **Backup phase**
![](/assets/blockchain-security-general-wallet-security-01.png)
![](/assets/blockchain-security-general-wallet-security-02.png)
![](/assets/blockchain-security-general-wallet-security-03.png)


# Securing Your Wallet
- Careful with online services
- **Small amounts**
- **Backup** wallet
  - Encrypt online backups
  - Use many **secure** locations
  - Regular backups
- **Encrypt** your wallet
  - Never forget password
  - **Strong password**
- Offline wallet for savings
- Keep software **up to date**
- **Multi-signature**
![](/assets/blockchain-security-securing-your-wallet-01.png)


# Cold Storage
- Keeping crypto **offline**
- **Security** precaution
- Dealing with **large amounts**
- Example
  - Exchange **instant withdrawal**feature
  - Minimize the possibility - stealing entire reserve in a **security breach**
  - Amount
    - Keeping majority in **cold storage**
    - Cover anticipated withdrawals - **kept on the server**
![](/assets/blockchain-security-cold-storage-01.png)


# Cold Wallets
- **Generates** and **stores** private wallet keys **offline**
- **Unsigned transactions**are generated **online**
- Transferred **offline** for **verification and signing**
- **Signed transaction**is transferred **online**
- Funds managed offline in **Cold storage**
  - Security precaution
  - Dealing with large amounts
- Protected against online threats
  - **Viruses** / **trojans** / **hackers**
- Similar to hardware wallets
![](/assets/blockchain-security-cold-wallets-01.png)


# Protect Cryptocurrencies
- **Hard** and **long password**
- Two-factor authentication **(2FA)**
- **Diversify**: split your funds in several locations
- Keep cryptocurrency **off the internet**
- **Decentralized exchanges**
  - Do not hold user’s funds
![](/assets/blockchain-security-protect-cryptocurrencies-01.png)


<!-- # Two Factor Authentication (2 -->
- Time-based One-time Password (**TOTP**)
  - Most commonly used 2FA
  - One-time generated code is entered
  - Identity verified – **share**d secret
  - Same hash (HMAC) generated by the two sides
  - Secret can be exposed during the registration
- Universal Second Factor (**U2F**)
  - No shared secret
  - Public key cryptography
  - Server knows the **public key**
  - User knows the **private key**
  - No confidential databases stored by the server
  - Potential attacks against individual users


# Two Factor Authentication: TOTP Scheme
![](/assets/blockchain-security-two-factor-authentication-totp-scheme-01.png)


# Two Factor Authentication: U2F Scheme
![](/assets/blockchain-security-two-factor-authentication-u2f-scheme-01.png)


# Server-Side Security

```cs
Never Store Private Keys on the Server!
```

![](/assets/blockchain-security-server-side-security-01.png)


# Server-Side Security for Crypto Projects
- Assume your server **might be hacked**soon or later
  - **External**attack: hackers, exploits in third party components, etc.
  - **Internal** attack: developers and admins already have access
- Design the system so that hacker cannot steal money
  - **Cold wallet**&rarr; holds most of the crypto-assets (e.g. > 99%)
  - **Hot wallet**&rarr; holds operational funds (e.g. < 1%)
  - Use **multi-signature** schemes to send payments
  - Use **smart contracts**to collect payments and **sign them offline**


# Server-Side Security: Bad Practice
- A server-side component holds the server wallet's **private key**
  - The server wallet **holds all the funds**for the entire system
  - **Very bad idea**!
- Hacker / developer / admin takes the key
  - All funds controlled by the key are **stolen**
- Example: CoinCheck
![](/assets/blockchain-security-server-side-security-bad-practice-01.png)


# Server-Side Security: Good Practice
- A server-side component holds a **limited power private key**
  - The associated address holds **small balance** (to pay the gas price)
  - It can prepare & sign transactions for **further processing**
  - Prepared transactions hold proof coming from the client-side
- A few other machines **verify** the prepared transactions
  - Then multi-signatures are created with hardware wallets
- If the hacker / developer / admin takes the key
  - Funds cannot be stolen, only fake transaction can be created
![](/assets/blockchain-security-server-side-security-good-practice-01.png)


# Multi-Signature Wallets
- Multi-signature wallets
  - To sign a transaction, **several signatures**are required
  - First signature created at the **server-side**
  - Second signature, created at the **client side**
- To send a transaction, both **server + client should cooperate**
  - Hackers need to hack the server + the client in the same time
- Implementation in Bitcoin:
  - BIP-45 - Deterministic P2SH Multisignature Wallets


# **Famous Blockchain Disasters**
- The DAO Hack, Parity Hacks, Tether Token Hack, Bitcoin Gold Scam, etc.
![](/assets/blockchain-security-famous-blockchain-disasters-01.png)


# The DAO Hack
- Decentralized Autonomous Organization
- **Codify** the rules and decision making apparatus
- **splitDAO** allows you to **move your funds**to another DAO
  - **Calls its fallback function**
- **Credits** the other DAO **before debiting**your account (**bad idea**)
- From the **other** DAO, **call back**intosplitDAO, **until all funds drained**
- **Entire Story**
![](/assets/blockchain-security-the-dao-hack-01.png)


# The Parity Wallet Hack
- Parity wallet offers **multiple options**to store tokens and Ether
- Simple **public/private key-pairs**
- **Smart contracts**which manage assets 
- Wallets are **controlled by code**
- **Multi-signature wallets**- allow for transaction logging, withdrawal limits, and rule-sets for signatures required
![](/assets/blockchain-security-the-parity-wallet-hack-01.png)


# First Parity Multisig Hack Wallet Explanation
- **Constructor** uses the following utility method to initialize wallet:
- But there’s a function that does “dynamic dispatch”
- Just encode a call to **initWallet**
- Entire Story 


# First Parity Multisig Hack Wallet Solution
- Not extracting the constructor logic into the library contract altogether
- Not using **delegatecall** as a catch-all forwarding mechanism 
![](/assets/blockchain-security-first-parity-multisig-hack-wallet-solution-01.png)


# Second Parity Multisig Hack Wallet Explanation
- Parity’s multisig wallet 
  - Instead of inheritance, deploy 1instance of the “parent class”
    - Done to reduce gas usage
    - Just leave it **uninitialized**
  - Somebody **initialized** it
  - Entire Story
![](/assets/blockchain-security-second-parity-multisig-hack-wallet-explanation-01.png)


# CoinDash ICO Hack
- **Payment and shipment**startup 
- Web server **compromised**
- **Hacker changed ETH address**
- Stole 43,000 ETH
  - **$7 million**
- Returned 10,000 ETH
- **Entire Story**
![](/assets/blockchain-security-coindash-ico-hack-01.png)


# Enigma Project Scam
- Compromised
  - Website
  - Mailing lists 
  - Administrator account 
- **Fake token pre-sale**
- Defrauding potential investors of more than **1,500 ethers**
- The hijacked accounts promised a **large return on investment**
- Funds were **not recovered**
- **Entire Story**
![](/assets/blockchain-security-enigma-project-scam-01.png)


# Tether Token Hack
- Dollar-pegged cryptocurrency **Tether**
- **$30+ million** was stolen from the U.S
- Tokens were taken from their virtual treasury 
- Sent to an unknown **bitcoin address**
- Company moved to **blacklist** the tokens stolen through an update to the **Omni protocol**
![](/assets/blockchain-security-tether-token-hack-01.png)


# Bitcoin Gold Scam
- **Fake wallet**
- Website’s operators 
  - Stole $3+ million in **bitcoin**, **bitcoin gold**, **ethereum** and **litecoin**
  - No relationship with **Bitcoin gold’s development team**
  - Initially claimed the site was **hacked**
  - **Wiped their GitHub**
  - **Ceased responding**to users on Slack channel
![](/assets/blockchain-security-bitcoin-gold-scam-01.png)


# NiceHash Market Breach
- NiceHash - **cryptocurrency mining marketplace**
- About **4,700** bitcoin stolen
- Employee’s computer -**compromised**
- Perpetrator gain access 
- **Takes Bitcoin**
![](/assets/blockchain-security-nicehash-market-breach-01.png)


# Coincheck Exchange Hack
- Japanese exchange Coincheck was hacked in Jan 2018
  - http://fortune.com/2018/01/31/coincheck-hack-how/
  - Nearly $500 million stolen
- All assets were in **hot wallet** (connected to Internet machine)
- No **multi-signature**was used for the hacked hot wallet
  - Just steal the private key and transfer the assets to hacker's address


# IOTA Cryptography Hack
- First rule of cryptography:
- Wrote their own **hash function** (Curl-P)
  - Claim it was for a **good reason**
  - IOTA does calculations in **base-3** (balanced ternary)
  - Normally **no benefit** to this
- **Broken** by cryptographers from MIT and Boston University
  - Using **differential cryptanalysis**
  - **Alter signed transactions** without invalidating the signature, by finding **hash collisions**
- **Switched to a base-3 variant of Keccak (“parent” of SHA-3)**
- **don’t write your own**


# Verge “time warp” attack
- **Timestamps** as far back **in the past**as allowed
- Network responded by **reducing the mining difficulty**
  - For the **specific mining algorithm**the attacker was targeting
    - Verge has **5 different algorithms**, each with a separate difficulty setting, to fight against ASIC miners
    - This meant **instead of 50% attack, 10% attack was enough**
- **Mined a lot of XVG**in a very short amount of time
- **Difficulty adjustment**algorithm **didn’t do its job**
  - The one in Bitcoin, where the difficulty is adjusted **every 2016 blocks**instead of every block, **would have been better**


# Double-spend attacks
- Due to **low network hashrate**
  - BTG, ZEN, CANN, EFL, QTL, WBB, UNB, BTA
- Due to **power in hands of pool employees**and **accepting 0-confirmation transactions**
  - BTC (GHash.io attacking BetCoin Dice)
- Due to a **bug**
  - USDT
![](/assets/blockchain-security-double-spend-attacks-01.png)


# Summary
- **Vectors of attack** – cryptography, networking, consensus, wallets and keys, 2FA, phishing and scam, server hacks, smart contracts
- **Blockchain** – each block connected to **blocks before**and**after**and secured through **cryptography**
- **Wallets** – careful with online services, **backup**, use hardware
- **Exchanges**– decentralized, 2FA, diversify
- **Blockchain's disasters** – The DAO Hack, Parity Wallet Breach and Freeze, CoinDash ICO Hack, Enigma ProjectScam, Tether Token Hack, Bitcoin Gold Scam, NiceHashMarket Breach, Coincheck, IOTA, XVG, double spends
![](/assets/blockchain-security-summary-01.png)



