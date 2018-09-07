# Implementing the Node and its API

...
# Designing the Blockchain Node
## Node, Chain, Blocks, Transactions, Genesis Block, Mining, Peers and Synchronization

# Table of Contents
- Blockchain System **Architecture**
  - Keys, Addresses, Coins, Balances, Genesis Block
  - Designing the REST API
- Building the **Blockchain Node**
  - Implementing the **Blocks**
  - Implementing the **Transactions**,Addresses, and Balances
  - Implementing the **Mining** Process
  - **Peers**, Synchronization and Consensus
![](/assets/designing-the-blockchain-node-table-of-contents-01.png)
![](/assets/designing-the-blockchain-node-table-of-contents-02.png)


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


# Keys and Addresses
- **Elliptic curve cryptography**(ECC), using the **secp256k1** curve
- private key
- privKey
- public key
- = privKey * G
- address
- = ripemd(pubKey)


# Coins and Rewards
- **Coins** are 64-bit integers (no real numbers!)
  - 1 **coin** = 1 000 **milli-coins** = 1 000 000 **micro-coins**
- All transfers, fees, block awards are defined in **micro-coins**
- The **block reward**(per mined block) is **static**
  - 5 000 000 micro-coins
- The **minimum transaction fee**(to avoid spam) is
  - **10**micro-coins


# The REST API
- For simplicity, implement a simple **RESTful API**
- Default listening **HTTP port**&rarr; 5555
- The **host** is the external hostname / IP address of the node

```cs
GET / POST
```



# Blockchain Network: REST API
- https://stormy-everglades-34766.herokuapp.com
![](/assets/designing-the-blockchain-node-blockchain-network-rest-api-01.png)


# Building the **Blockchain Node**
- Chain, Blocks, Transactions, Addresses, Balances, Peers & Sync, Designing the REST API
![](/assets/designing-the-blockchain-node-building-the-blockchain-node-01.png)


# Building the Blockchain Node
- Holds peers + network communication (**REST API**for simplicity)
- Each node is uniquely identified by its **NodeId**and has public **URL** for its REST API
- **Node**


# Building the Blockchain
- Holds the blocks + transactions
  - Also serves as a **mining pool**
  - Consensus algorithm: **proof of work**(SHA256 hashing)
  - The **chain with most work**(~ the longest) is the main chain 
- **Blockchain**


# REST Endpoints: Info
- **nodeId** == unique node ID (based on **datetime** + **random**)
- **chainId** == the **hash** of the **genesis block**(identifies the chain)
- Nodes can provide additional info by choice

```cs
GET
```



<!-- # REST Endpoints: Debug Info (All Node Da -->

```cs
GET
```

- Provide as much info as possible (to simplify debugging)


# REST Endpoints: Debug &rarr; Reset Chain

```cs
GET
```

- Use this endpoint for debugging / testing purposes only
- It should **reset the entire chain**to its initial state
  - Blocks, transactions, balances &rarr; reset to the genesis block
  - All transactions and balances will be **lost** (except the genesis transactions)
  - Peers &rarr; keep all connections


# Implementing Blocks

```cs
Chained Blocks Holding Transactions
```

![](/assets/designing-the-blockchain-node-implementing-blocks-01.png)


# Building the Blockchain Node: Blocks
- **Block**
- Assigned by the miners


# Calculating the Block Data Hash
- The **block data hash**is calculated by **SHA256** hashing the **JSON** representation of following block fields (in exactly this order):
  - '**index**'
  - '**transactions**', each holding these fields:
    - '**from**', '**to**', '**value**', '**fee**', '**dateCreated**', '**data**', '**senderPubKey**', '**transactionDataHash**', '**senderSignature**', '**minedInBlockIndex**', '**transferSuccessful**'
  - '**difficulty**', '**prevBlockHash**', '**minedBy**'


# REST Endpoints: All Blocks

```cs
GET
```



# REST Endpoints: Block by Number

```cs
GET
```



# The Genesis Block – The Start of the Chain
- The **genesis block** has **index** = **0**
- It has no miner: **mined by**= "**0000…00**", **difficulty** = 0, **nonce** = **0**
  - The **genesis date**is a fixed constant (the chain birthday)
- Holds the **initial faucet transaction**(fill the faucet with initial coins)

```cs
{
  "index": 0, "transactions": [ … ], "difficulty": 0,
  "minedBy": "0000000000000000000000000000000000000000",
  "blockDataHash": "15cc5052fb3c307dd2bfc6bcaa05763225…cefc",
  "nonce": 0, "dateCreated": "2018-01-01T00:00:00.000Z",
  "blockHash": "c6da93eb4249cb5ff4f9da36e2a7f8d0d6199…cc47f"
},
```



# Implementing Transactions

```cs
Transactions Transfer Some Value / Data
```

![](/assets/designing-the-blockchain-node-implementing-transactions-01.png)


# Building the Blockchain Node: Transactions
- **Transaction**
- Assigned when a new block is mined


# The Faucet Transaction in the Genesis Block
- Send initially some coins to the **faucet address**in the genesis block, so it to be able to fund the other addresses

```cs
{
  "from": "0000000000000000000000000000000000000000",
  "to": "f3a1e69b6176052fcc4a3248f1c5a91dea308ca9",
  "value": 1000000000000, "fee": 0,
  "dateCreated": "2018-01-01T00:00:00.000Z",
  "data": "genesis tx",
  "senderPubKey": "000000000000000000000000000000000000…00",
  "transactionDataHash": "8a684cb8491ee419e7d46a0fd24…ecc2",
  "senderSignature": ["0000…00","0000…00"],
  "minedInBlockIndex": 0, "transferSuccessful": true
}
```



# REST Endpoints: Get Pending Transactions

```cs
GET
```



# REST Endpoints: Get Confirmed Transactions

```cs
GET
```



# Calculating the Transaction Data Hash
- The **transaction data hash**uniquely identifies a transaction
  - Like in Etherscan: https://etherscan.io/tx/0xb03b6c7ef5c555001b41c32e5ac2c600c5e2c72b6918b3d68c0f3dd4b5cb54a8
- Calculated by the transaction data fields only:
  - '**from**', '**to**', '**value**', '**fee**', '**dateCreated**', '**data**', '**senderPubKey**'
  - Does not include the **signature** and **execution info**(the mined block index + success of the execution)
- **Pending** and **unsigned** transactions also have data hash (**unique ID**)


# REST Endpoints: Get Transaction by Hash

```cs
GET
```

- The last two fields appear only after the transaction is mined 


# REST Endpoints: List All Account Balances

```cs
GET
```

- Lists all **accounts** that have non-zero **confirmed balance**
  - The all-zeros-address (the genesis address) will have negative balance


# REST Endpoints: List Transactions for Address
- **All transactions**, associated with the given **address** are returned
  - **Confirmed** transactions (successful or not) + **pending** transactions
  - Order the transactions by **date and time** (ascending)
  - Pending transactions will not have **minedInBlockIndex**

```cs
GET
```



# REST Endpoints: Get Balances for Address
- The address **balance** is calculated by iterating over **all transactions**
  - For each block and for each successful transaction for the specified address, matching the confirmations count, sum the values received + spent + fees

```cs
GET
```

- The safe confirm count = 6


# Balances for Address
- Each address has 3 types of balances
  - **safeBalance** – 6 confirmations or more confirmations
  - **confirmedBalance** – 1 or more confirmations
  - **pendingBalance** – expected balance (0 confirmations)
    - It is assumed that all pending transactions will be successful
- Each successful **received** transaction **adds value**
- All **spent** transactions subtract the transaction **fee**
- Successful **spent** transactions **subtract value**


# REST Endpoints: Balances Invalid for Address
- Return **zero** balances for **non-active** addresses (no transactions)
- For invalid addresses:
  - Return "**404 Not Found**" with **errorMsg** = "**Invalid address**"

```cs
GET
```



# Creating a Transaction
- To **create** a transaction you need:
  - **Sender public key**– 65 hex digits; **Recipient address**(to) – 40 hex digits
  - Transfer **value** – positive integer; **Fee** for the miners – positive integer
  - **Date & time** (to avoid replay attacks) – **ISO8601** UTC datetime string
  - Transaction **data**(payload / comments) – optional string
- The **sender's address** (from) is extracted from the sender public key

```cs
{ "from": "c3293572dbe6ebc60de4a20ed0e21446cae66b17",
  "to": "f51362b7351ef62253a227a77751ad9b2302f911",
  "value": 25000, "fee": 10, "dateCreated": "2018-02-10T17:53:48.972Z",
  "senderPubKey": "c74a8458cd7a7e48f4b7ae6f4ae9f56c5c88c0f03e7…bba1"
}
```



# Signing a Transaction
- To **sign** a transaction, a **private** + **public key**are required
- First, put the transaction data in a **JSON object** (without signature)
  - Fields order: '**from**', '**to**', '**value**', '**fee**', '**dateCreated**', '**dat а**', '**senderPubKey**'
- The **from address**should always match the sender **public key**
- Remove any whitespace, calculate **SHA256** and **sign** it
  - When the '**data**' field is empty, remove it from the JSON

```cs
{
  "from": "c3293572dbe6ebc60de4a20ed0e21446cae66b17",
  "to": "f51362b7351ef62253a227a77751ad9b2302f911", "value": 25000,
  "fee": 10, "dateCreated": "2018-02-10T17:53:48.972Z", "data": "funds",
  "senderPubKey": "c74a8458cd7a7e48f4b7ae6f4ae9f56c5c88c0f03e…bba1"
}
```



# Signing a Transaction – Example
- Sender's **private key**:
- Corresponding **public key**(compressed):
- Sender **address**:
- Sample **transaction data**(still not signed):

```cs
{ "from": "c3293572dbe6ebc60de4a20ed0e21446cae66b17",
  "to": "f51362b7351ef62253a227a77751ad9b2302f911", "value": 25000,
  "fee": 10, "dateCreated": "2018-02-10T17:53:48.972Z", "data": "funds",
  "senderPubKey": "c74a8458cd7a7e48f4b7ae6f4ae9f56c5c88c0f03e7…bba1" }
```



<!-- # Signing a Transaction – Example -->
- JSON-serialized **transaction data**for signing (whitespace removed):
- **Transaction data hash** for signing (SHA-256):
- ECDSA **signature** of the above hash (signed signature bytes):
- The ECDSA signature consists of **2 * 64 hex digits**(2 * 256 bits)

```cs
{"from":"c3293572dbe6ebc60de4a20ed0e21446cae66b17","to":"f51362b7351ef62253a227a77751ad9b2302f911","value":25000,"fee":10,"dateCreated":"2018-02-10T17:53:48.972Z","data":"funds","senderPubKey":"c74a8458cd7a7e48f4b7ae6f4ae9f56c5c88c0f03e7c59cb4132b9d9d1600bba1"}
```



<!-- # Signing a Transaction – Example -->
- Signed transaction (the data hash + signature added in the JSON):
- Use **deterministic ECDSA signature**, based on the curve **secp256k1**and RFC-6979 with **HMAC-SHA256**

```cs
{ "from": "c3293572dbe6ebc60de4a20ed0e21446cae66b17",
  "to": "f51362b7351ef62253a227a77751ad9b2302f911", "value": 25000,
  "fee": 10, "dateCreated": "2018-02-10T17:53:48.972Z", "data": "funds",
  "senderPubKey":
    "c74a8458cd7a7e48f4b7ae6f4ae9f56c5c88c0f03e7c59cb4132b9d9d1600bba1",
  "transactionDataHash": "6a3a7859c389bad17d79c5856e17a74daecfa6d…467e",
  "senderSignature": [
    "33be705476889fbb647633a9272cf546401f22e87f0c2b2a6c58ff56b7aa368a",
    "66722e9b58a05952a986ee2c90faa1cc828575503cfc393278006629f20bd78c"
  ]
}
```



# REST Endpoints: Send Transaction
- The transaction as accepted by the Node only after successful validation

```cs
POST
```



# Send Transactions
- For each received transaction the Node does the following:
  - Checks for missing / invalid **fields** / invalid field **values**
  - Calculates the transaction **data hash**(unique transaction ID)
    - Checks for collisions &rarr; **duplicated transactions**are skipped
  - Validates the transaction **public key**, validates the **signature**
  - Checks the sender account **balance** to be **>= value + fee**
  - Checks whether **value >= 0**and **fee > 10**(min fee)
  - Puts the transaction in the "**pending transactions**" pool
  - Sends the transaction to **all peer nodes** through the REST API
    - It goes from peer to peer until it reaches the entire network


# REST Endpoints: Send Transaction &rarr; Error
- In case of **error**, the response holds a JSON object with human-readable error message (like shown above)

```cs
POST
```



# Implementing Mining

```cs
Proof-of-Work Mining
```

![](/assets/designing-the-blockchain-node-implementing-mining-01.png)


# Implementing the Mining: Get Mining Job
- Nodes act like **mining pools**
  - Prepare the**next block candidate**for mining and give it to the miners
  - **Miners** submit back the **mined hash + nonce + timestamp**to the Node

```cs
GET
```



<!-- # The Coinbase Transaction (Rewa -->
- A special **coinbase transaction** is inserted before all transactions in the candidate block, to transfer the **block reward + fees**
  - The sender address, sender public key and signature are zeroes

```cs
{ "from": "0000000000000000000000000000000000000000",
  "to": "9a9f082f37270ff54c5ca4204a0e4da6951fe917",
  "value": 5000350, "fee": 0, "dateCreated":
    "2018-02-10T17:53:48.972Z", "data": "coinbase tx",
  "senderPubKey": "000000000000000000000000000000000000…0000",
  "transactionDataHash": "4dfc3e0ef89ed603ed54e47435a18b…176a",
  "senderSignature": ["0000000000…0000", "0000000000…0000"],
  "minedInBlockIndex": 35, "transferSuccessful": true,
}
```



# How to Calculate the Block Data Hash?
- Nodes prepare **block candidates**and calculate their **data hash**
  - Use **JSON representation of the block** data (no whitespace)
    - Fields order: "**index**", "**transactions**", "**difficulty**", "**prevBlockHash**" (when exists), "**minedBy**"
  - **Dates** should come as text, in ISO-8601 format
  - **Hex numbers**are always written in lowercase, e.g. **c6af**, not **C6AF**
  - The JSON data is hashed using SHA256

```cs
string json = toJSON(block_data)
string block_data_hash = SHA256(json)
```





# Transactions in the Block Candidates
- Each **transaction** in the block candidate (after processing) is represented as a JSON object like this:

```cs
{
  "from": "44fe0696beb6e24541cc0e8728276c9ec3af2675",
  "to": "9a9f082f37270ff54c5ca4204a0e4da6951fe917",
  "value": 25000, "fee": 10, "dateCreated":
  "2018-02-10T17:53:48.972Z", "data": "party: 50% prepayment",
  "senderPubKey": "2a1d79fb8743d0a4a8501e0028079bcf82a4f…eae1",
  "transactionDataHash": "4dfc3e0ef89ed603ed54e47435a18b…176a",
  "senderSignature": ["e20c…a3c29df79f", "cf92…0acd0c2ffe56"],
  "minedInBlockIndex": 73, "transferSuccessful": true
}
```



# The Mining Process: Preparation
- When a **Miner** requests a **block for mining**, the node prepares it:
  - Creates the **next block candidate**: executes all pending transactions and adds them in the block candidate + inserts a coinbase tx
  - Calculates the **block data hash** and provides it to the miner
  - The Node keeps a **separate block candidate for each mining request**
    - It holds **map< blockDataHash** **&rarr; block>**
  - If a miner requests a block candidate **again**, the Node sends an **updated block**(eventually holding more transactions)
  - The Node will always return the **latest block for mining**, holding the **latest pending transactions**(to collect maximum fees)


# The Mining Process: Trying Many Hashes
- The miner changes the **nonce** + **timestamp** in a loop until it finds a **SHA256 hash**starting with **d** zeroes (**d** == **block difficulty**)
  - The Miner submits the **mined block hash**to the Node
  - 1-2 times per second the minermay take an **updated block candidate** from the Node
  - Miners may start several**parallel threads**tospeed-up the mining
- **Block Candidate**


# Building the Miners Hash
- Calculating the block hash:
- Example of block data for hashing (by the miners):
- The hash is a **proof-of-work** of difficulty 5 (starts with 5 zeroes)


# Processing a Mined Block
- Miners submit their **mined block hash**(+**date**+**nonce**)
  - Node builds the mined block and propagates it through the network
- When a miner submits a **proof-of-work hash**
  - The node finds the block candidate by its **blockDataHash**
  - The node **verifies the hash**+ its **difficulty** and **builds** the next block
    - The block candidate is **merged** with the **nonce** + **timestamp** + **hash**
  - Then if the block is **still not mined**, the **chain is extended**
    - Sometimes other miners can be faster &rarr; the mined block is expired
  - Then all **peers are notified**about the new mined block


# Implementing the Mining: Submit Block

```cs
POST
```



# Implementing the Mining: Submit Invalid Block

```cs
POST
```



# The Mining Pool in the Nodes
- Internally nodes implement a simple **mining pool**
  - Consists of **mining jobs** (block candidates sent to the miners)
- Each **mining job**has a **blockDataHash** and belongs to some **miner**
  - The **coinbase transaction**in the job is assigned to the miner's address
- After a **new block is mined**in the network (by someone)
  - All pending mining jobs are **deleted** (because are no longer valid)
  - When a miner submits a mined block later &rarr; 404 "Not Found"
- MiningJobs: map<blockDataHash &rarr; Block candidate>


# REST Endpoints: Debug &rarr; Mine a Block

```cs
GET
```

- Use this endpoint for debugging / testing purposes only. Example:
- It should **mine** the pending transaction and **create the next block**
- Executes the entire mining process: get mining job &rarr; calculate valid proof-of-work hash &rarr; submit the mined job


# Network Difficulty: Static or Dynamic?
- The **network difficulty**in each block candidate
  - Specifies the **number of leading zeroes** in the expected mined block SHA256 hash, e.g. **5**leading zeroes
- Difficulty might be a **constant** number (hard-coded in the nodes)
- Advanced developers might **adjust the difficulty over the time**using some calculations to target a fixed number of seconds between blocks
  - For example, if the **target block time**== **5** seconds
  - For the next block, the difficulty can be dynamically adjusted:
    - If **average block time**for the entire chain **< 5** &rarr; **difficulty++**
    - If **average block time**for the entire chain **> 5**&rarr; **difficulty--**


# Peers and Synchronization
![](/assets/designing-the-blockchain-node-peers-and-synchronization-01.png)
![](/assets/designing-the-blockchain-node-peers-and-synchronization-02.png)
![](/assets/designing-the-blockchain-node-peers-and-synchronization-03.png)
![](/assets/designing-the-blockchain-node-peers-and-synchronization-04.png)


# REST Endpoints: List All Peers
- **Peers** are described by their unique **nodeId** and **URL**
  - **map(nodeId &rarr; url )**
- Each node is connected to a few neighbor peers
  - Not to all peers in the network

```cs
{
  "162269f6993d2b5440dddcd6": "http://localhost:5556",
  "162266dff5753a87a3e72403": "http://af6c7a.ngrok.org:5555",
}
```



# REST Endpoints: Connect a Peer

```cs
{
  "message":
      "Connected to peer: http://212.50.11.109:5556"
}
```

- Always keep the connections **bi-directional**
  - If Alice is connected to Bob, then Bob should also be connected to Alice


<!-- # REST Endpoints: Connect a Peer (Inval -->

```cs
{
  "errorMsg":
      "Already connected to peer: http://212.50.11.109:5556"
}
```

- If a node is **already connected**to given peer, return "**409 Conflict**"
- If the **chain ID** does not match, don't connect, return "**400 Bad Request**"


# Connecting to a Peer
- To **avoid double-connecting** to the same peer
  - First get **/info** and check the **nodeId**
  - Never connect twice to the same **nodeId**
- To **ensure bi-directional connections**
  - When Alice is connected to Bob, try to connect Bob to Alice
  - First check for existing connection: get **/info** and check the **nodeId**
- After successful connection to a peer, try to **synchronize the chain**(if the peer has better chain) + **synchronize the pending transactions**


# Synchronizing the Chain & Pending Txs
- **Synchronizing the chain**from certain peer
  - First **get** **/info** and check the peer's chain **cumulative difficulty**
  - If the peer chain has bigger difficulty, **download** it from **/blocks**
  - **Validate** the downloaded peer chain (blocks, transactions, etc.)
  - If the peer chain is valid, **replace the current chain**with it
  - **Notify all peers**about the new chain
- **Synchronizing the pending transactions**from certain peer
  - Download **/transactions/pending** and append the missing ones
  - Transactions with the same **hash** should never be **duplicated**


# Validating a Chain
- When a **chain** is downloaded from a peer, it needs be **validated**
- Validate the **genesis block** &rarr; should be exactly the same
- **Validate each block** from the first to the last
  - Validate that all **block fields**are present and have valid values
  - **Validate the transactions**in the block
    - Validate transaction **fields** and their **values**, recalculate the **transaction data hash**, validate the **signature**
    - Re-execute all transactions, re-calculate the values of **minedInBlockIndex** and **transferSuccessful** fields


<!-- # Validating a Chain -->
- **Validate each block** from the first to the last (cont.)
  - Re-calculate the **block data hash**and **block hash**for each block
  - Ensure the **block hash**matches the **block difficulty**
  - Validate that **prevBlockHash**  == the **hash** of the previous block
- Re-calculate the cumulative difficulty of the incoming chain
- If the cumulative difficulty > current cumulative difficulty
  - **Replace the current chain**with the incoming chain
  - Clear all current mining jobs (because they are invalid)


# Calculating the Cumulative Difficulty
- Difficulty **0** == 0 leading zeroes &rarr; **every** hash works well
- Difficulty **1** == 1 leading zero &rarr; **1/16** of hashes work
- Difficulty **2** == 2 leading zero &rarr; **1/256** of hashes work
- …
- Conclusion: difficulty **p** is **16 times**more difficult than **p-1**
- **Cumulative difficulty**== how much **effort** is spent to calculate it
  - **cumulativeDifficulty** == 16 ^ **d 0** + 16 ^ **d 1** + … 16 ^ **d n**
  - where **d 0**, **d 1**, … **d n** are the individual difficulties of the blocks


# REST Endpoints: Notify Peers about New Block
- A peer should **notify** all its connected **peers** when
  - A **new block**is mined or new valid block is received from some peer
  - A **chain of higher difficulty** was arrived (synchronized) from other peer

```cs
{ "message": "Thank you for the notification." }
```



# Notifying all Connected Peers
- A node **sends notification**to all its connected peers when a **change in the chain** occurs
  - If the chain **cumulative difficulty is increased**(new block is mined / better chain is received)
- The notified node should check whether the new block ends to a **better chain**(based on the cumulative difficulty) and then accept the new chain
  - The new chain is downloaded from **nodeUrl/blocks** (using an additional HTTP request)
  - This notification might be also sent over a **Web Socket**


# Deleting Lost Peers
- Extra: implement functionality to **delete lost peers**
  - If a peer is contacted and it does not respond, delete it from the connected peers
- If **/info** does not return the correct **peerId**
  - It is invalid or does not respond &rarr; delete it
- You may run this check once per minute or when you send a notification about a new block




