# Implementing the Wallet App

...
# Building a Blockchain:Wallet, Faucet, Block Explorer
## Designing and Building theWallet App + Faucet App + Blockchain Explorer

# Table of Contents
- Blockchain Network: System **Architecture**
- Building a **Wallet**App
  - HD Wallet vs. Simple Keystorevs. Just "Enter the Private Key"
- Building a **Faucet** App
- Building a **Block Explorer** App
- Testing the Blockchain Network
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-table-of-contents-01.png)
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-table-of-contents-02.png)


# Blockchain System Architecture

```cs
Nodes, Miners, Faucet, Wallets, Explorer
```

- Node
- Wallet
- Block Explorer
- Miner
- Node
- Node
- Faucet


# Blockchain System Architecture
- **Node**
- **Wallet**
- **Miner**
- **Block Explorer**
- **Faucet**


# Blockchain Network: REST API
- https://stormy-everglades-34766.herokuapp.com
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-blockchain-network-rest-api-01.png)


# Building the **Blockchain Node**
- Chain, Blocks, Transactions, Addresses, Balances, Peers & Sync, Designing the REST API
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-building-the-blockchain-node-01.png)


# Building the Blockchain Node
- Holds peers + network communication (**REST API**for simplicity)
- Each node is uniquely identified by its **NodeId**and has public **URL** for its REST API
- **Node**


# Building the Blockchain
- Holds the blocks + transactions
  - Also servers as a **mining pool**
  - Consensus algorithm: **proof of work**(SHA256 hashing)
  - The **chain with most work**(~ the longest) is the main chain 
- **Blockchain**


# Implementing Blocks

```cs
Chained Blocks Holding Transactions
```

![](/assets/building-a-blockchain-wallet-faucet-block-explorer-implementing-blocks-01.png)


# Building the Blockchain Node: Blocks
- **Block**
- Assigned by the miners


# Calculating the Block Data Hash
- The **block data hash**is calculated by **SHA256** hashing the **JSON** representation of following block fields (in exactly this order):
  - '**index**'
  - '**transactions**', each holding these fields:
    - '**from**', '**to**', '**value**', '**fee**', '**dateCreated**', '**data**', '**senderPubKey**', '**transactionDataHash**', '**senderSignature**', '**minedInBlockIndex**', '**transferSuccessful**'
  - '**difficulty**', '**prevBlockHash**', '**minedBy**'


# Keys and Addresses
- **Elliptic curve cryptography**(ECC), using the **secp256k1** curve
- private key
- privKey
- public key
- = privKey * G
- address
- = ripemd(pubKey)


# Wallet App

```cs
Generating & Storing Keys, Check Account Balances, Signing & Sending Transactions
```

![](/assets/building-a-blockchain-wallet-faucet-block-explorer-wallet-app-01.png)


# Choosing the Wallet Type
- HD Wallet vs. Simple Keystore vs. Just "Enter the Private Key"
- **HD wallet**
  - Based on BIP39 and BIP44 standards (mnemonic + key derivation)
  - Holds multiple keys + addresses
- **Simple keystore**
  - A private key encrypted in a JSON / UTC document
- Very simple: "**just enter your private key**"
- **Password-protect** all wallet operations, e.g. sign a transaction


# The Wallet App: Sample Screenshots
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-the-wallet-app-sample-screenshots-01.png)
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-the-wallet-app-sample-screenshots-02.png)


<!-- # The Wallet App: Sample Screenshots -->
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-the-wallet-app-sample-screenshots-2-01.png)
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-the-wallet-app-sample-screenshots-2-02.png)


# Wallet App
- The **Wallet App**is console / desktop / mobile / web application
  - Manages private keys + signs and sends transactions
  - It might be based on the **HD wallet**standards (BIP-39 / BIP-32)
  - Or for simplicity, could hold just a **single private key**
- Functionality:
  - Create **new wallet**/ open **existing wallet**(optionally protect it with **password** and keep it in the app / browser local storage)
  - Check **account balance**for certain blockchain address
  - **Create**, **sign** and **send** transactions


# Faucet App

```cs
Creating a Faucet Web App
```

![](/assets/building-a-blockchain-wallet-faucet-block-explorer-faucet-app-01.png)


# Faucet App
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-faucet-app-01.png)
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-faucet-app-02.png)


# The Faucet App
- The **Faucet App**is web applications that holds some coins
  - E.g. donated from the **genesis transaction**
  - Or mined by someone and donated to the faucet
- The faucet works **like a wallet**with hard-coded private key
- It sends 1 coin (or less) to anyone who requests coins
  - Limits: **one request per address per hour**+ **captcha**
- For each request, the faucet creates a **transaction**, **signs** it and **sends** it to the specified node URL (through HTTP POST)


# Block Explorer

```cs
Web App to Explore Blocks,Transactions, Accounts, Balances
```

![](/assets/building-a-blockchain-wallet-faucet-block-explorer-block-explorer-01.png)


# Block Explorer
- Implement the Block Explorer as **Web app** (at port **9999**)
  - Optionally, it may hold the **Faucet App**functionality inside
- Block Explorer functionality:
  - View **blocks**
  - View **confirmed** transactions
  - View **pending** transactions
  - View accounts and **balances**
  - View **peers**
  - View **network difficulty**


# How to Test the Blockchain?
- Important Test Scenarios to Consider
![](/assets/building-a-blockchain-wallet-faucet-block-explorer-how-to-test-the-blockchain-01.png)


# Testing the Blockchain: Node + Wallet + Miners
- Run and test the **Node**
  - Test all its REST endpoints
- Run and test the **Wallet**
  - The creating new wallet + opening existing wallet
  - Send transactions (valid / invalid) and check the balances
- Run and test the **Miner**
  - Ensure it works correctly and produces valid chain blocks
  - Run several miners and ensure they behave correctly


# Testing the Blockchain Network: Peers
- A sample scenario to test the blockchain network **p2p sync**
  - Run 4 nodes:
    - http://localhost:5555 | http://localhost:5556 | http://localhost:5557 | http://localhost:5558
  - Connect them into two separate networks:
    - http://localhost:5555 ↔ http://localhost:5556
    - http://localhost:5557 ↔ http://localhost:5558
  - Mine in the first node; Mine in the last node
  - Connect the two separate network &rarr; check how the higher difficulty chain wins the consensus and the other nodes lose their chain


# Testing the Blockchain: Faucet + Explorer
- Run and test the **Faucet**
  - Test the faucet &rarr; send coins to certain address
  - Try to be greedy &rarr; the faucet should reject you
- Run and test the **Block Explorer**
  - Explore the blocks, mined transactions, pending transactions
  - Explorer the accounts and balances
  - Explore the peers (view peers / connect to different peers)
- Implement **automated testing** for the Node + other components
  - Unit tests + integration tests + system tests




