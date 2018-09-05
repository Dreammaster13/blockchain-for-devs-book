# Blockchain Concepts
## Blocks, Chains, Consensus, Mining, Transactions, Problems in Blockchain
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-01.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-02.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-03.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-04.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-05.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-06.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-07.png)
![](/assets/blockchain-concepts-blocks-chains-consensus-mining-transactions-problems-in-blockchain-08.png)


# Table of Contents
- Blocks, Chains & Hashes
- The Byzantine Generals Problem
- Public Key Cryptography
- Consensus Algorithms
- Transactions, Fees & Priority
- Double-spending Problem
- The 51% Blockchain Attack
![](/assets/blockchain-concepts-table-of-contents-01.png)


# Blocks, Chains & Hashes
![](/assets/blockchain-concepts-blocks-chains-hashes-01.png)


# Blockchain == Chain of Data Blocks
- timestamp
- block_hash
- all_transactions_hash
- transaction #1
- hash
- transaction #2
- hash
- transaction #3
- hash
- prev_hash
- nonce
- timestamp
- block_hash
- all_transactions_hash
- transaction #1
- hash
- transaction #2
- hash
- transaction #3
- hash
- nonce
- prev_hash
- timestamp
- block_hash
- all_transactions_hash
- transaction #1
- hash
- transaction #2
- hash
- transaction #3
- hash
- prev_hash
- nonce
![](/assets/blockchain-concepts-blockchain-chain-of-data-blocks-01.png)
![](/assets/blockchain-concepts-blockchain-chain-of-data-blocks-02.png)


# Blocks
- In blockchain the **blocks**are created by the **miners** / **validators**
  - Bitcoin blocks: https://blockchain.info/blocks 
  - Ethereum blocks: https://etherscan.io/blocks
  - Each block holds a set of **transactions**
- **Block time**== the time between two blocks
  - From few seconds to few hours
  - **Bitcoin**: average block time = **8-10 minutes**
  - **Ethereum**: average block time = **12-15 seconds**
- timestamp
- block_hash
- all_transactions_hash
- transaction #1
- hash
- transaction #2
- hash
- transaction #3
- hash
- nonce
- prev_hash


# The Byzantine Generals Problem
- Decentralized Solution
![](/assets/blockchain-concepts-the-byzantine-generals-problem-01.png)


# The Byzantine Generals Problem
- An army of **generals**want to attack a city
  - Only a well **coordinated attack**at the same time will succeed
  - Some generals are **loyal** and want to reach agreement
  - Some generals are **traitors** and may vote sub-optimally
    - Including voting differently to different destinations
  - Nobody knows **who is loyal**and who is a **traitor**
- Find an **algorithm** to reach stable consensus


# How does Blockchain solve it?
- **Public Key Cryptography**
- Use cryptography tosign/verify transactionsin a blockchain network
- **Consensus Algorithms**
- Agree on a common consensus for the operations in the network
![](/assets/blockchain-concepts-how-does-blockchain-solve-it-01.png)
![](/assets/blockchain-concepts-how-does-blockchain-solve-it-02.png)


# Public Key Cryptography
- Private Keys, Public Keys, Addresses…
![](/assets/blockchain-concepts-public-key-cryptography-01.png)


# Public Key Cryptography Concepts
- **Public key cryptography**prevents fake messages by **signing**
- In blockchain the **public key cryptography**is used
  - **Private key**is used to sign messages
  - **Public key**is used to verify the signature of given message
  - The sender **address** is derived from the owner's public key
- If a participant sends coins to another participant, **the transaction is signed**by the sender's **private key**
  - Everyone on the network can **verify** the sender's signature


# Public / Private Keys & Blockchain
- private key
- public key
- address
- transaction
- signature
- signed transaction
- valid / invalid


# Bitcoin Keys and Addresses
- Sample **private key**: 256-bit number (Base58 encoded)
- The corresponding **public key** (uncompressed): 2 * 256 bits
- The same **public key** (compressed): 257-bit number (hex encoded)
- Corresponding **Bitcoin address**: 160-bit hash (Base58 encoded)


# Consensus and Consensus Algorithms
- Proof-of-Work & Proof-of-Stake
![](/assets/blockchain-concepts-consensus-and-consensus-algorithms-01.png)


# Why a Consensus Algorithm is Needed?
- **Consensus algorithms**in a blockchain network
  - Select the **winning node**to create the **next block**(in fair way)
- The winning node (winning miner):
  - Is **awarded** some new coins (e.g. 12.5 BTC) for its effort 
  - Selects the pending transactions **to be included**in the next block
  - Creates the next block and **propagates** it in the network
- The entire network **validates** the new block
  - Either **accept it** (when it is valid) or reject it
  - If the block is **valid**, build their own blocks **on top of it**


# Consensus Algorithms
- **Consensus algorithms**choose the **next block creator**
  - In a **fair way**, that everyone in the network agrees on
  - The chain with the **most work** or **highest stake** represents **network consensus** (Satoshi’s explanation: https://tinyurl.com/satgenerals)
- **Proof-of-work ( PoW )**algorithms
  - Nodes compete to find a solution to a heavy cryptographic puzzle
  - Used in Bitcoin, Ethereum, Litecoin, Zcash, Monero, Bitcoin Gold
- **Proof-of-stake ( PoS )**algorithms and others
  - The next creator is selected randomly, proportionally to its stake in the network, used in EOS, Cardano, NEO, Lisk, Stellar, Qtum, …


# **Proof-of-Work ( PoW )**
- **Proof-of-work ( PoW )**algorithms
  - Challenge all nodes to solve a **cryptographic puzzle**(work)
    - Requires heavy and expensive computations + equipment + power
    - Example: find a number **nonce**, such that**SHA256(prev_block_hash + transactions + nonce)** < **target**
    - The number **target** is known as "**network difficulty**"
  - The node first solved the puzzle is the **winner**
    - It **creates the next block**and takes some coins as award
    - The solution acts as **proof-of-work**, verified by the other nodes
![](/assets/blockchain-concepts-proof-of-work-pow-01.png)


# **Proof-of-Stake ( PoS )**
- **Proof-of-stake ( PoS )**algorithms
  - Use transaction **validators**instead of **miners**
  - Small **hardware** needs and **power** consumption
  - A node becomes a **validator** by locking some coins (**stake**)
- PoS selects the **next block creator**among all validators
  - Many flavors of proof-of-stake &rarr; many PoS consensus algorithms
  - Select random next validator / select several candidates and perform voting on their proposed chains to select one of them
![](/assets/blockchain-concepts-proof-of-stake-pos-01.png)


# Transactions, Fees & Priority
![](/assets/blockchain-concepts-transactions-fees-priority-01.png)


# Transactions
- **Transactions** hold information about fund transfers


# Transaction Fees and Priorities
- Each block can hold a limited set of transactions
  - Only a **subset** of the pending transactions is mined
  - Limited by the network **block size** and miner's choice
  - The other transactions are left for the next blocks
- Miners decide which transactions to include in each block
  - Based on their **fee** and **priority**
  - The **fee** is assigned by the **sender**
  - The **priority** increases with the transaction **age**
![](/assets/blockchain-concepts-transaction-fees-and-priorities-01.png)
![](/assets/blockchain-concepts-transaction-fees-and-priorities-02.png)


# Transaction Speed
- Transaction **speed** depends dramatically on the fee
  - **High-fee** transactions are processed **faster**
  - **Small-fee** transactions are processed **slower**
  - Some transactions are never processed (e.g. no fee)
- Blockchain networks mine blocks at different speed
  - **Bitcoin**users may pay very **high fees**(hundreds of dollars) and wait for many hours, see https://bitcoinfees.earn.com
  - **Ethereum** transactions run **faster**, within seconds, with lower fees
  - Some networks have almost **real-time** transactions (e.g. Bitshares)
![](/assets/blockchain-concepts-transaction-speed-01.png)


# Double Spending Problem
- How does the Blockchain solve it?
![](/assets/blockchain-concepts-double-spending-problem-01.png)


# Double Spending Problem
- **Double spending problem** == spend certain amount twice
  - Easy to prevent through a **central authority**(single database)
  - More complex in **decentralized systems**like Bitcoin and Ethereum
- Blockchain prevents double spending
  - The blockchain holds **signed chain of blocks**with transactions
  - All **pending transactions**are collected in the network nodes
  - A **single node**creates the **next block**(selected by a consensus)
  - The **next block creator**puts the pending transactions (after validation) in the next block (and prevents double spending)


# Mining the Next Block
- Transaction A
- Transaction B
- Transaction C
- Transaction …
- Blockchain Node #1
- Blockchain Node #2
- Blockchain Node #...
- Blockchain Node #7
- Next (New) Block


# The 51% Blockchain Attack
![](/assets/blockchain-concepts-the-51-blockchain-attack-01.png)


# Network Splits
- 105
- 106
- 107
- 108
- 106
- 107
- 108
- 109
- 110
![](/assets/blockchain-concepts-network-splits-01.png)
![](/assets/blockchain-concepts-network-splits-02.png)
![](/assets/blockchain-concepts-network-splits-03.png)
![](/assets/blockchain-concepts-network-splits-04.png)
![](/assets/blockchain-concepts-network-splits-05.png)
![](/assets/blockchain-concepts-network-splits-06.png)
![](/assets/blockchain-concepts-network-splits-07.png)
![](/assets/blockchain-concepts-network-splits-08.png)
![](/assets/blockchain-concepts-network-splits-09.png)
![](/assets/blockchain-concepts-network-splits-10.png)


# Joining Split Networks
- 105
- 106
- 107
- 108
- 106
- 107
- 108
- 109
- 110
![](/assets/blockchain-concepts-joining-split-networks-01.png)
![](/assets/blockchain-concepts-joining-split-networks-02.png)
![](/assets/blockchain-concepts-joining-split-networks-03.png)
![](/assets/blockchain-concepts-joining-split-networks-04.png)
![](/assets/blockchain-concepts-joining-split-networks-05.png)
![](/assets/blockchain-concepts-joining-split-networks-06.png)
![](/assets/blockchain-concepts-joining-split-networks-07.png)
![](/assets/blockchain-concepts-joining-split-networks-08.png)
![](/assets/blockchain-concepts-joining-split-networks-09.png)
![](/assets/blockchain-concepts-joining-split-networks-10.png)
![](/assets/blockchain-concepts-joining-split-networks-11.png)
![](/assets/blockchain-concepts-joining-split-networks-12.png)


# The 51% Attack
- Attackers holding more than 50% of the hash power could potentially **reverse-back transactions**(and double-spend money)
![](/assets/blockchain-concepts-the-51-attack-01.png)


# The 51% Attack and Confirmations Count
- More **confirmations**== less chance for reversing blocks
- In Bitcoin at least **6 confirmations**are considered safe
- In Ethereum **12 confirms**are safe
![](/assets/blockchain-concepts-the-51-attack-and-confirmations-count-01.png)


# Summary
- **Blockchain** is a **distributed ledger**with chained **blocks & hashes**
- Blockchain solves the Byzantine Generals Problem + Double Spending Problem
  - **Public / private key**cryptography + **consensus** algorithms
- Proof-of-Work vs. Proof-of-Stake
- **Blocks** are created by miners and hold transactions
- **Transactions** have senders, recipients, amounts, fees
- Transaction **speed** depends on the **fees**
- **The 51% Attack**can rewrite blockchain transactions
![](/assets/blockchain-concepts-summary-01.png)


# Blockchain Concepts
- http://academytoken.com




