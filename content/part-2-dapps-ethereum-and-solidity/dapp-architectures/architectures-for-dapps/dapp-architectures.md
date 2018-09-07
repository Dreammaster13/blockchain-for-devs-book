# DApps: Architectures, Components, Wallets, Client-Side and Server-Side Interaction with the Blockchain

## DApps: Architectures, Components, Wallets, Client-Side and Server Side Interaction with the Blockchain

# Table of Contents
- **Architectures** for Decentralized Apps
- The **Ethereum DApps**Ecosystem: Nodes, Providers, Wallets
- Accessing the Wallet in a DApp
  - Server-Side Interaction with the Blockchain (**Server Wallet**)
  - Client-Side Interaction with the Blockchain (**JS Wallet**)
  - Client-Side Interaction through **MetaMask**
  - **Multi-Signature** Wallets
![](/assets/dapps-architectures-table-of-contents-01.png)


# DApp Architectures

```cs
Front-End, Back-End, Wallet Access
```

![](/assets/dapps-architectures-dapp-architectures-01.png)


# Decentralized Computing
- **Traditional Model**
- CPU + DB + storage: **local** or in a **data center**Payments: fiat moneyMonetization: ads
- **DApp Model**
- **decentralized** logic + DB + storage + …Payments: crypto
- Monetization: token mechanics
- **Cloud Model**
- **cloud** servers + **cloud** DB + **cloud** storagePayments: fiat money
- Monetization: ads
![](/assets/dapps-architectures-decentralized-computing-01.png)
![](/assets/dapps-architectures-decentralized-computing-02.png)
![](/assets/dapps-architectures-decentralized-computing-03.png)


<!-- # Decentralized Blockchain Apps (DAp -->
- **DApps**
- Hold **code** + **data** on the blockchain / p2p network
- The front-end is still a traditional app
- **Client App**(front-end)
- **Smart Contract Backend**Code + data on the blockchain
- **Traditional Backend**Server-side code + data
![](/assets/dapps-architectures-decentralized-blockchain-apps-dapps-01.png)


# DApp Components
- Decentralized **logic**
  - **Smart contracts**(Ethereum), **chaincode** (Hyperledger)
- Decentralized **storage** (images, documents, videos, files)
  - IPFS / Storj / Swarm / other
- Decentralized **database** (Create / Read / Append / Burn)
  - BigChainDB
- Decentralized **messaging**
  - IPFS pub-sub


<!-- # DApp Components -->
- **Front-end** app (UI)
  - JavaScript app / mobile app / desktop app – the DApp UI
- **Wallet**
  - Client-side wallet / MetaMask / server-side wallet
  - Beware: user's private keys should never go to the server
- **Server-side** app
  - Still no mature decentralized PaaS exists
  - Beware: server-side logic is centralized


# The Ethereum DApp Ecosystem
![](/assets/dapps-architectures-the-ethereum-dapp-ecosystem-01.png)


# Web3 API: Connecting to Ethereum
- Web3 API (for JavaScript)
  - https://github.com/ethereum/wiki/wiki/JavaScript-API 
- Nethereum (for C#)
  - https://github.com/Nethereum/Nethereum
- Web3J (for Java)
  - https://github.com/web3j/web3j
- web3.py (for Python)
  - https://github.com/ethereum/web3.py
![](/assets/dapps-architectures-web3-api-connecting-to-ethereum-01.png)


# Server-Side Interaction with the Blockchain
- **_Note_:** the server-side wallet signs all transactions &rarr; it might be subject to hard **hacker attacks**&rarr; don't keep large amounts in it!
- **Client App**(front-end)
- **Backend App**
- (JS / Java / C# / Python / PHP / Ruby / Go / …)
![](/assets/dapps-architectures-server-side-interaction-with-the-blockchain-01.png)
![](/assets/dapps-architectures-server-side-interaction-with-the-blockchain-02.png)
![](/assets/dapps-architectures-server-side-interaction-with-the-blockchain-03.png)
![](/assets/dapps-architectures-server-side-interaction-with-the-blockchain-04.png)


# Sample Scenario for Server-Side Interaction
- Document Registry DApp
  - **Goal**: keep a set of authentic documents on the blockchain
  - **Users**can view / verify documents, published on the blockchain
    - PDF documents hosted in **IPFS** (decentralized storage)
    - Document **hashes** published in a smart contract
  - **Admins** can upload new documents
    - Blockchain transactions are signed at the **server-side**
    - Encrypted server-side wallet, unlocked by admin's password


# Client-Side Interaction with the Blockchain
- Using a client-side JS wallet (e.g. LightWallet / Ethers.js) simplifies the interaction and delegates the security risks to the end-users
- **Client App**(front-end)
- **Backend App**
- (JS / Java / C# / Python / PHP / Ruby / Go / …)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-01.png)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-02.png)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-03.png)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-04.png)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-05.png)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-06.png)
![](/assets/dapps-architectures-client-side-interaction-with-the-blockchain-07.png)


# Client-Side JS Wallet
- User registers in a mobile app / Web app
- A **client-side wallet** is created during the registration
  - The **wallet JSON**is stored in the app / browser's **LocalStorage**
    - Strong **encryption** (Scrypt), based on strong password
  - Optionally the wallet JSON can be **stored at the server-side** or in **Dropbox** / **Storj** (readable by key-derived from the password)
- Security assumptions:
  - The user's password and private key **never leave the client app**!
  - All **transactions are signed client-side**, never at the server-side!


# Sample Scenario for Client-Side JS Wallet
- Crypto Travel Service
  - **Users** register in the system and **get a wallet** (private key + address)
    - The **wallet JSON**is stored **client-side**, strongly encrypted (users can backup it in case of damaged / lost device)
    - The wallet password / private key never leave the client app
  - **Transport providers**also register and **get a wallet**
    - **Request payments** via QR code, e.g. inside the bus / train / taxi
  - **Users pay for transport**service using a mobile app (via the QR code)
    - Transfer the requested ETH to the payment contract
  - **Transport providers**get their ETH from the contract upon request


# Client-Side Interaction through MetaMask
- **Client App**(front-end)
- Use MetaMask to protect private keys and sign transactions client-side
- MetaMask is currently **unavailable on mobile devices**!
- **Backend App**
- (JS / Java / C# / Python / PHP / Ruby / Go / …)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-01.png)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-02.png)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-03.png)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-04.png)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-05.png)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-06.png)
![](/assets/dapps-architectures-client-side-interaction-through-metamask-07.png)


# Sample Scenario for MetaMask Interaction
- The CryptoKitties Game
  - **Goal**: view, purchase, breed and sell collectable items (kitties)
    - https://www.cryptokitties.co
  - **Site visitors** can browse the kitties, published on the blockchain
    - Server-side logic reads the kitties from the blockchain
  - **Registered users**can purchase / sell kitties
    - **MetaMask** is used to **sign transactions**/ interact with smart contracts
    - MetaMask addon provides "**Injected Web3 API**" inside the browser


# Multi-Signature Interaction with the Blockchain
- **Client App**(front-end)
- **Backend App**
- (JS / Java / C# / Python / PHP / Ruby / Go / …)
- **Verifier**
- **Verifier**
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-01.png)
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-02.png)
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-03.png)
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-04.png)
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-05.png)
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-06.png)
![](/assets/dapps-architectures-multi-signature-interaction-with-the-blockchain-07.png)


# Multi-Signature Interaction with the Blockchain
- For increased security **multi-signature wallets**can be used
  - A multi-signature Ethereum wallet is a special smart-contract
  - Example: https://github.com/gnosis/MultiSigWallet
- **Functionality**of multi-signature wallets
  - Configure wallet **owners** + **number of signatures**
  - **Submit** a new transaction { **address** + **value** + **data** } &rarr; **id**
  - **Confirm** / **revoke** transaction by **id**
  - **Execute** transaction by **id** (after confirmed by enough owners)


# Sample Scenario for Multi-Signature
- Crypto Marketplace
  - **Sellers** put some items for sale
  - **Users**pay to the **marketplace multi-sig wallet address**
  - **Users**confirm the purchased items were delivered
  - Then the marketplace adds a **payout transaction**:
    - Multi-sig wallet address &rarr; seller address
  - On a daily basis **another persons confirm**the waiting transactions
    - Finally, one person **sends** the confirmed transactions for the day


# Exercise: Simple Voting System
- Using Ethereum, Solidity, Ethers.js, Node.js
![](/assets/dapps-architectures-exercise-simple-voting-system-01.png)


# Multi-Signature Wallet

```cs
https://wallet-website.gnosis.pm
```

![](/assets/dapps-architectures-multi-signature-wallet-01.png)


# Summary
- DApps hold **logic** + **database** + **storage** in a decentralized way
  - Using blockchain / peer-to-peer technologies
- **Decentralized apps**on the Ethereum blockchain may implement
  - Server-side interaction with the blockchain (**server wallet**)
  - Client-side interaction with the blockchain (**JS wallet**)
  - Client-side interaction with the chain through **MetaMask**
  - **Multi-signature** interaction with the blockchainthrough a multi-sig wallet contract
![](/assets/dapps-architectures-summary-01.png)




