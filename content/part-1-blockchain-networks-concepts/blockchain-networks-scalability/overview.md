# Chapter 1.9. Scalability of Blockchain Networks: Sharding, Sidechains, Offchain Transactions, Payment Channels, State Channels

# Table of Contents
- Solving the **scalability** and **performance** problems
  - Towards **fast transactions**and **high throughput**
- **Off-chain** transactions and **payment channels**
  - **Hashed Time-Locked Contracts (HTLC)**
  - Payment networks and the **Lightning Network**
- **Cross-chain** transactions and **atomic swaps**
- **Sidechains**(parallel blockchain networks)
- **Sharding**
- **SegWit**
![](/assets/scaling-the-blockchain-networks-table-of-contents-01.png)
![](/assets/scaling-the-blockchain-networks-table-of-contents-02.png)


# Solving the Scalability and Performance Problems
- Fast Transactions, Block Size, Scalable Storage
![](/assets/scaling-the-blockchain-networks-solving-the-scalability-and-performance-problems-01.png)


# Bitcoin Scalability: Problems
- **Bandwidth**and **block-time** in Bitcoin
  - **1 MB megabyte**per block 
  - About **10 minutes** per block
  - Removing this limit requires a “**hard fork**”
  - Changes are backward-incompatible
- The high processing **fees**
- The tendency of **centralization**
  - Larger needs for **storage**, **bandwidth**, and **computational power**
![](/assets/scaling-the-blockchain-networks-bitcoin-scalability-problems-01.png)


# Bitcoin Scalability: Current Limits
- **1 MB block**
  - **7 transactions**per second @ **250 bytes**/**tx**
  - ~220 million **transactions** per year
  - **Not** **enough** for a city, let alone the world
- **Number of transactions per second**(TPS) Bitcoin can handle:
![](/assets/scaling-the-blockchain-networks-bitcoin-scalability-current-limits-01.png)


# Blockchain Scalability: Estimations
- **1 billion transactions**per day
  - 1.6 GB **blocks** (1655 MB)
  - 87 **terabytes/year**(87029089 MB)
  - Maybe enough for a **large metro area**
- **7 billion people**doing**2 blockchain transactions**per day
  - **24 GB**blocks
  - **3.5** TB / day
  - **1.27** PB / year
![](/assets/scaling-the-blockchain-networks-blockchain-scalability-estimations-01.png)


# Trends Toward Centralization
- Bigger blocks == **centralization**
  - Very few **full nodes**
  - Very few **miners**
  - De facto **inability** to **validate blockchain**
- Danger of 50% + 1 **attacks**
  - More than **50%** of the hashpower is owned by just few entities
  - Solution: **more individual miners**
  - But Satoshi’s gentleman’s agreement about GPUs is clearly over: https://bitcointalk.org/index.php?topic=12.msg54#msg54 
![](/assets/scaling-the-blockchain-networks-trends-toward-centralization-01.png)


# Growth **Space** Trend: Blockchain Size
- Bitcoin full nodes must store the **entire blockchain**
  - Transaction validation requires **entire history**
- The blockchain is about**170 GB**in size (as of June 2018)
  - Downloading the blockchain peer-to-peer takes a **few days**
![](/assets/scaling-the-blockchain-networks-growth-space-trend-blockchain-size-01.png)


# Exponential Growth **Space** Trend
- A logarithmic data unveils
  - ~ **1.8 x boost**in the **size** of the blockchain**every year**
- **Growth space**holds back many small participants
  - Thus increases **centralization**
![](/assets/scaling-the-blockchain-networks-exponential-growth-space-trend-01.png)


# Improving the Scalability and Performance
- Many technologies improve the scalability and TX throughput
  - **Faster consensus**, e.g. **DPoS** is faster than **PoW**
  - Increased **block-size** and improved protocols, e.g. **SegWit**
  - **Offchain transactions**: HTLC, payment channels, payments networks, state channels, cross-chain transactions
  - **Sidechains**: parallel blockchain networks, connected to the main
  - Blockchain **sharding**: split the chain into several sub-chains (shards), running in parallel by different subsets of the nodes
  - Consensus **without blockchain**: HashGraph, Tangle, Holochain, …


# Off-Chain Transactions
- Payment Channels and Lighting Network
![](/assets/scaling-the-blockchain-networks-off-chain-transactions-01.png)


# Off-Chain Transactions
- Promising more **speed** and **volume**
  - **Payments** done directly with minimal fee
- **Independent**
  - **Separate** from the main chain, limited damage on the chain
- Offers more **privacy**(e.g. if use Zerocash)
  - **Transactions** not stored in the **transaction history**
  - Cannot be **tracked** anymore
- Flexible: new **innovations** and **design** can be implemented
![](/assets/scaling-the-blockchain-networks-off-chain-transactions-01.png)


# What are "Payment Channels"?
- **Payments channels**
  - Allow **two participants**to send transactions to each other
    - Without hitting the main blockchain
  - Rely on a **locked deposit**to guarantee fair operations
  - Use **multi-signatures**
  - Do not require direct **trust**
- Main chain
- A
- B


# Payment Channels: Concepts
- Two parties want to send **off-chain payments**
  - **Deposit**some money (e.g. in a smart contract) – **on-chain**
  - Sign and send many **off-chain transactions**
  - In case of **dispute**, the smart contract decides upon the signed proofs each party provides
  - **Closing transaction**: finalizes the balances – **on-chain**
- Once created, payment channels can execute **unlimited** number of instant direct transactions
- See **https://raiden.network/101.html**


<!-- # Hashed Time-Lock Contract (HT -->
- Hashed Time-Lock Contract (**HTLC**)
  - Off-chain payment protocol
  - Allows two parties to directly send funds using cryptography
- HTLC combines two other concepts:
  - **Hash-lock**
    - To receive a payment, the recipient unlocks other's party payment
  - **Time-lock**
    - Locked funds are spent within certain time, or returned back


# Payment Channel Networks: Concepts
- Payment channels can connect each other in a **graph**
  - A **payment channel network** uses **routing** between channels
- Inside the payment channel network all participants can **transact off-chain**, multi-hop, at almost **no cost**
![](/assets/scaling-the-blockchain-networks-payment-channel-networks-concepts-01.png)


# Lightning Network
- The **lightning network** is an **off-chain micropayment**system
  - Makes transactions work **faster** using **payment channels**
  - Conceptualized by **Joseph Poon**and **Tadge Dryja**
  - Aimed to solve the **block size limit**and the **transaction delays**
- **Lightning Network** operates on top of **Bitcoin**
  - Often referred to as “**Layer 2**” network
- **Raiden Network** operates on top of **Ethereum**
  - Similar concept, but for Ethereum (ETH & ERC20 tokens)
![](/assets/scaling-the-blockchain-networks-lightning-network-01.png)


# Key Storage
- **Keys** are generated using **BIP-32** HD wallets
  - **Pre-generated** by both parties   
  - Generated in a **Merkle tree**, **very deep**within the tree
- Each key can be a **child of the previous key**
  - For example, there can be many **sub-keys** for day 1
  - This key is used as a **master key**for all keys generated on day 1
- By disclosing private keys pre-arranged, it is possible to **invalidate millions of old transactions**with only a few kilobytes of data
- Core channels in the Lightning Network can conduct billions of transactions **without** a need for **significant storage costs**
![](/assets/scaling-the-blockchain-networks-key-storage-01.png)


# Unidirectional Channel
- Alice wants to **send coins** to Bob
- Alice and Bob have **MultiSig channel**
- First**Alice**gets a**refund**,**signed by Bob**,**unlocked after 30 days**
- Then **Alice sends** 1 BTC to the **MultiSig address**
- Even if **Bob** disappears, she can **get the coins back** after 30 days when the **time expires**
- Alice and Bob MultiSig Channel
- 1 BTC
- Alice
- 1 BTC
- Alice Refund Address
- 1 BTC


<!-- # Unidirectional Channel -->
- With no lock time **Alice sends 0.1 BTC to Bob**and**0.9 to herself**
  - Transaction **isn't** **signed** by **Bob** yet 
- Then **Alice sends 0.2 BTC to Bob**and**0.8 to herself**
  - **Bob sees**the first transaction, but doesn't sign it
- The channel over and **Bob** **signs** the transaction
  - If **Bob doesn't sign**Alice get her coins**back** when the **time expired**
- Alice
- 1 BTC
- Alice and Bob MiltiSig Channel
- 1 BTC
- Alice Refund Addess
- 1 BTC
- Alice
- 0.9 BTC
- Bob
- 0.1 BTC
- Alice
- 0.8 BTC
- Bob
- 0.2 BTC


# Bidirectional Channel
- With **29 days** lock time **Alice sends 0.1 BTC to Bob**and**0.9 to herself**
  - The channel has **two** nLock times 
- Then **Alice sends 0.2 BTC to Bob**and**0.8 to herself**
  - **Bob**wants to send 0.1 BTC to Alice so, **get back**the first transaction
- Any time the transaction **is brought back**, the time **goes closer** to the end day
- When Alice and Bob **both sign**, the channel is **closed**
- Alice
- 1 BTC
- Alice and Bob MiltiSig Channel
- 1 BTC
- Alice Refund Addess
- 1 BTC
- Alice
- 0.9 BTC
- Bob
- 0.1 BTC
- Alice
- 0.8 BTC
- Bob
- 0.2 BTC
- Bob
- 0.1 BTC
- Alice
- 0.9 BTC


# 3 Party Payments
- **Alice** wants to pay **Carol**, they **both** have a channel open with **Bob**
- **Alice** sends 0.01 BTC to **Bob** via **off-chain transaction**
- **Bob** sends 0.01 BTC to **Carol**
  - Problem: **Bob**can**keep the coins for himself**, and**Carol**can clime**she never got**the coins
- Alice
- Bob
- Carol


# Hash-Locked Contracts
- Using **one-way hash**functions, **Alice** can **prove** she sent funds to **Carol** **off-chain**
- Pay to Contract
  - Knowledge of **secret R hashed**into **hash H** proves receipt
  - Receiver **signs** a contract stating if **R** is **disclosed** funds have been **received**


# Hash-Locked Contracts – Example
- Carol chooses a **random number R**, and keeps it **secret**
- She computes the hash of R, **hash (R) = H**
- Carol**sends H**to Alice (secure, off-chain)
- Alice sends **0.01 BTC** to a new output: **Bob & hash160(H)**
  - To spend it, Bob **needs** to know **R**
- Alice
- Carol
- Bob
- Bob sends **0.0 1 BTC**to Carol & **H**
- Carol **redeems** Bob’s transfer, **revealing R**
- Bob now knows **R**and can **spend**Alice’s transfer
- The **coins have gone**from Alice to Carol via Bob 


# Problems With Hash-Locked Contracts
- If Carol **refuses to disclose R**, she will hold up the channel between Alice and Bob
  - If her **channel expires**after Alice and Bob’s she can **steal funds**by redeeming the hashlock
- Bob **has to be rich**for this to really work
- 3rd party **low-trust multisig** and/or **extremely** small values sent can mostly work today
- Alice
- Carol
- Bob


<!-- # Hashed Time-Lock Contract (HT -->
- If Bob can produce to Alice **input R**from**hash H**within**3 days**, Alice will pay Bob 0.01 BTC
- The above clause is void after **3 days**
- Either party may agree to settle terms using other methods if **both agree**
- Violation of terms incurs a **maximum penalty**of funds in this contract
- Bob
- (Payment)
- Alice
- (Refund)
- HTLC Output
- 0.01 BTC


<!-- # Bitcoin Lightning Network (Part -->
- **Alice**wants to send funds to **Dave**via**Bob**and**Carol**
- **Dave** sends **Alice** **hash H** produced from random data R
- **Alice** & **Bob** create an HTLC output in the payment channel to pay **Bob** **0.01 BTC**, with a **3-day nLockTime** refund back to **Alice**
- Alice
- Carol
- Bob
- Dave
- **Bob** & **Carol** create an HTLC output in the payment channel to pay **Carol** 0.01 BTC, with a **2-day** nLockTime refund back to **Bob**
- **Carol** & **Dave** create an HTLC output in the payment channel to pay **Dave** 0.01 BTC, with a **1-day** nLockTime refund back to **Carol**
  - **Dave**can now get 0.01 BTC if he **discloses R** to **Carol**


<!-- # Bitcoin Lightning Network (Part -->
- **Dave** discloses **R** to **Carol** within 1 day 
  - **Carol** now has enough information to pull funds from **Bob**
- **Carol**and**Dave**agree to update the balances in the channel instead of broadcasting on the blockchain
- **Carol discloses R**to**Bob**within 2 days
  - **Bob**now has enough information**to pull funds from Alice**
- Alice
- Carol
- Dave
- Bob
- **Bob**and**Carol**agree to update the balances in the channel instead of broadcasting on the blockchain
- **Bob discloses R**to**Alice**within 3 days
  - **Alice**can prove she sent funds to **Dave**
- **Alice** and **Bob** agree to update the balances in the channel instead of broadcasting on the blockchain


# Broken Chanel & Disputes
- If**Bob**and**Carol**don’t cooperate, **Carol**immediately closes out the channel and broadcasts all pending transactions in the channel onto the **blockchain**
- **Carol**redeems the 0.01 by disclosing the HTLC output and R on the Bitcoin **blockchain**
- **Bob**observes R from the blockchain and can pull money from **Alice** off-chain
- Blockchain
- Alice
- Carol
- Dave
- Bob


# HTLC Implementations
- **HTLC** can be implemented in a smart contract system
  - **HTLC** implementation in Solidity for **ETH** and **ERC20** tokens: https://github.com/chatch/hashed-timelock-contract-ethereum
- Instant payments networks
  - Lightning Network for Bitcoin: http://lightning.network
  - Raiden Network for Ethereum: https://raiden.network
  - Nuo: https://getnuo.com/payments.html
  - QuickX: https://quickx.io/whitepaper/QuickXProtocolv1.7.pdf 


# State Channels
- A **generalization** of payment channels
- Update **arbitrary** state off-chain
  - Use **nonces** and **signatures** for **provable sequencing of updates**
  - Dispute resolution by an **on-chain smart contract**
- Useful for general-purpose blockchains, like Ethereum
- Example: play a **chess game**offchain and submit the winner on the chain at the end
![](/assets/scaling-the-blockchain-networks-state-channels-01.png)


# Connecting Blockchains

```cs
Cross-Chain Atomic Swaps
```

![](/assets/scaling-the-blockchain-networks-connecting-blockchains-01.png)


# Connecting Blockchains
- Cross-chain **atomic swaps**
  - Exchange funds between **two participants**, whose assets reside on **separate blockchains** (e.g. Bitcoin ↔ Litecoin)
  - **Swapping** cryptocurrencies **without a trusted third-party**
  - Execute a protocol that guarantees the **atomicity** of the transfer
  - The protocol should only have **two outcomes**, either participants **successfully exchange**assets, or **nothing happens**
  - **Neither** party can **cheat** the other


# Cross-Chain Transactions with HTLC
- **Hashed Time-Lock Contract (HTLC)**can work **cross-chain**
  - **Payment channels**open on both networks
  - **Time-lock** condition + **hash-lock** condition
- **Cross-chain atomic swaps**using **HTLC** are already supported by the Lightning Network
- Cross-chain trading allows tobuild **decentralized exchanges**
  - Example: exchangeunion.com
- See also: https://github.com/evbots/dex-protocols 
![](/assets/scaling-the-blockchain-networks-cross-chain-transactions-with-htlc-01.png)


# Cross-Chain Transactions
- Cross-chain **atomic swap**
- Alice Funding TX
- Bob Funding TX
- 3. Alice Commit TX Locked H(x) SigA
- 5. Bob Commit TX Locked H(x) SigB
- 2. Alice Refund TX SigAB
- 4. Bob Refund TX SigAB
- 7. Bob Claim TX Reveal x SigAB
- 6. Alice Claim TX Reveal x SigAB


# Sidechains
- Parallel Blockchain Networks
![](/assets/scaling-the-blockchain-networks-sidechains-01.png)


# What is "Sidechain"?
- **Sidechains**are separate blockchains bound to Bitcoin’s chain
  - Allow to receive and spend bitcoins using a **two-way peg**(**2WP**)
  - **2WP** == **lock** coins on a network + **unlock** the same on the other
- **Sidechaining** allows coins from one blockchain to be securely used within a completely **separate** blockchain
  - But still **moved back**to the original chain if necessary
- The **original chain**is normally referred to as the "**main chain**"
  - Any **additional blockchains**are referred to as "**sidechains**"


# Types of Sidechains
- **Federated** sidechains
  - Don’t require any changes to the Bitcoin consensus rules
  - Example: **The Elements Project**(elementsproject.org)
- **Merge-mined**sidechains
  - Use additional mining process + incentive system to implement additional functionality, e.g. smart contracts
  - Example: **RSK** (www.rsk.co)


# Plasma: Trees of Sidechains
- **Plasma** == blockchain of blockchains (tree)
  - **Tree of sidechains**
  - Each sidechain periodically commits its state to its **parent sidechain**
  - The **root chain**is some public blockchain, e.g. the **Ethereum** network
  - https://plasma.io/plasma.pdf
![](/assets/scaling-the-blockchain-networks-plasma-trees-of-sidechains-01.png)


# Sidechain Internals
- **Symmetric 2WP**
  - Consensus protocol to **lock** or **unlock** coins for **cross-transfer**
- Suppose the **secondary chain**has “**settlement finality**”
  - The **consensus** is reached when a fixed number of parties (the consensus group) **sign the block**containing the cross­-chain transfer transaction
- The **mainchain** takes **signed block**as the payload of a **main chain transaction**
  - Together with an **SPV proof** (Simplified Payment Verification)
  - The **secondary chain**consensus group unlocks the coins at the main chain




# Sidechain Example: RSK
- **RSK** is the first open source smart contract platform powered by the **Bitcoin network** 
  - Also **rewards** the **Bitcoin miners**via **merge-mining**
  - Miners are paid for executing smart contracts
- **RSK**adds functionality to the Bitcoin ecosystem
  - Smart-contracts
  - Instant payments
  - Higher-scalability
![](/assets/scaling-the-blockchain-networks-sidechain-example-rsk-01.png)


# How RSK System Works?
![](/assets/scaling-the-blockchain-networks-how-rsk-system-works-01.png)




# Blockchain Sharding

```cs
Splitting the Chain into Smaller Shards
```

![](/assets/scaling-the-blockchain-networks-blockchain-sharding-01.png)


# Blockchain Sharding
- **Sharding** == split the blockchain network state into **shards**
  - Just like big databases are sharded into several physical machines
  - Each shard holds **portion of the state** and processes portion of the **transactions**
- Example of public blockchain with sharding:
  - **Zilliqa** blockchain – https://zilliqa.com
  - Technical description: https://docs.zilliqa.com/whitepaper.pdf


<!-- # SegWit (Segregated Witne -->

```cs
A Bitcoin Protocol Improvement
```

![](/assets/scaling-the-blockchain-networks-segwit-segregated-witness-01.png)


# SegWit
- **Segregated Witness** == **SegWit**
  - **Segregate** means to **separate**
  - **Witnesses** are the transaction **signatures**
  - Implemented soft fork in the Bitcoin-based networks (BIP-141)
- SegWit improves the **scalability** of the Bitcoin network
  - Separated transaction signatures &rarr; **m ore transactions in a block**
- Implemented by currencies such as **Litecoin**,**Bitcoin Gold**, etc.
  - ~ **70% more transactions**for within the same block-size
![](/assets/scaling-the-blockchain-networks-segwit-01.png)


# SegWit
![](/assets/scaling-the-blockchain-networks-segwit-01.png)


# What is a Bitcoin Transaction?
- Source: https://en.bitcoin.it/wiki/File:TxBinaryMap.png
![](/assets/scaling-the-blockchain-networks-what-is-a-bitcoin-transaction-01.png)


# SegWit
- **SegWit** is **splitting** the transaction into **two segments**
  - Removing the unlocking signature ("**witness**" data) from the original portion
  - And appending it as a separate structure at the end

```cs
Inputs



```

- Outputs
- TXID Signatures
- TXID Signatures
- Amount Script
- Amount Script
- Signatures
- Signatures


# SegWit
- The **original section**would continue to hold the **sender** and **receiver data**
- And the **new "witness"**structure would contain **scripts and signatures**
-  The original data segment would be counted normally, but the **"witness" segment** would, in effect, **be counted as a quarter of its real size**


# Advantages of SegWit
- **Drop signatures**from relay
- Prune **old signatures**
- Solves all **unintentional malleability**


# Transaction Malleability
- **The signature**that goes along with the input data can be **manipulated**
- Inputs
- Outputs
- TXID Signatures
- TXID Signatures
- Amount Script
- Amount Script
- TXID Signatures
- TXID Signatures
- Which in turn can **change the transaction ID**
- It can make it **seem like the transaction didn’t even happen**in the first place


# Script Versions
- Instead of pushing the redeem script directly, **add a version byte**
  - **Witness** protected program
- **Unknown version** &rarr; anyone can spend
  - No longer restricted to redefining **OP_NOP opcodes**
  - All future Script changes become **soft forks**
  - Schnorr **signatures**, mast, value under signature

```cs
Inputs



```

- Outputs
- {v. “Script”}
- Inputs
- Outputs
- Amount Script
- Amount Script
- Witness
- Signature


# Script Versions
- Two **versions** defined immediately:
  - **v0** with the (**small**) redeem script in output
  - **v1** with the (**larger**) redeem script in witness
- Makes marginal **non-witness**size of out/in O(1)

```cs
Inputs



```

- Outputs
- {v. “Script”}
- Inputs
- Outputs
- Amount Script
- Amount Script
- Witness
- Signature


# SegWit Activation
- **SegWit**was activated on August 24, 2017
- Nonetheless, **most** Bitcoin network transactions **have not**begun to use the upgrade
- In the first week of October 2017, the proportion of network transactions**using SegWit**was 10%
![](/assets/scaling-the-blockchain-networks-segwit-activation-01.png)


# SegWit2X
- **SegWit2x** == **SegWit** + **2MB blocks**hard fork
  - Increase the **block size** and improve Bitcoin **scalability**
  - **SegWit2x**uses a **different** '**bit**' for signaling (bit 4 instead of bit 1) than SegWit
- **SegWit2x** didn't get enough support and was **canceled** by his creators on 8 November 2017
![](/assets/scaling-the-blockchain-networks-segwit2x-01.png)


# Bitcoin-NG
- A Scalable Blockchain Protocol
![](/assets/scaling-the-blockchain-networks-bitcoin-ng-01.png)


# Redesigning Blockchains for Scalability
- **Bitcoin-NG:**next-generation blockchain protocol
  - **Scalable blockchain protocol**created by: **Ittay Eyal**, **Adem Gencer**, **Emin Gün Sirer**, and **Robbert van Renesse** @ Cornell University
  - Implemented in the Waves Platform:https://waves-ng.wavesplatform.com
- Uses**multiple blocks per leader**
  - **Latency** is limited only by the propagation delay of the network
  - Its **bandwidth** is limited only by the processing capacity of the individual nodes


# EOS

```cs
New Blockchain Architecture
```

![](/assets/scaling-the-blockchain-networks-eos-01.png)


# EOS
- **EOS** == **blockchain architecture**designed to enable vertical and horizontal **scaling** of **decentralized applications**
  - Powerful decentralized platform for smart contracts
- The **EOS network** provides:
  - Accounts & authentication
  - Databases (JSON collections)
  - Asynchronous messaging
  - Scheduling of applications acrossmultiple CPU cores and/or clusters
![](/assets/scaling-the-blockchain-networks-eos-01.png)


# EOS
- The EOS blockchain architecture has the potential
  - To scale to **millions** of transactions per second
  - **Eliminates** user **fees**
  - Allows for quick and easy deployment of **decentralized applications**
  - **Testnet** launched in Sept / 2017
  - **Mainnet** expected in June / 2018
![](/assets/scaling-the-blockchain-networks-eos-01.png)


# Casper

```cs
Ethereum 2
```

![](/assets/scaling-the-blockchain-networks-casper-01.png)


# Casper: Transition to Proof-of-Stake
- Based on **Proof**-**of-Stake**(or similar) rather than **Proof-of-Work**
  - Mining will become **redundant**
  - The network post-Casper will rely on **stakers** and **staking pools**
  - **Stakers** will be rewarded for their service to the network
- Less resources will be wasted
  - Still attacks will be very expensive
- Expected to **reduce** the **inflation rate**: 14.75% &rarr; 2%


# Casper: Sharding
- Currently all Ethereum nodes process all transactions
  - A lot of resources are **wasted**
  - 30 000 nodes do the same duplicated work
- **Sharding**will allow **parallel transactions**, e.g.
  - A set of 100 nodes process 1000 txs
  - **In the same time**, other 100 nodes process other 1000 txs
  - Finally the results are **merged** into a single result
    - Conflicting transactions are handled properly


# Aeternity

```cs
Scalable Smart Contracts
```

![](/assets/scaling-the-blockchain-networks-aeternity-01.png)


# Aeternity
- Virtual machine for smart contracts + proprietary languages
- **State channels**for payments + smart contracts
- **Scalable** as long as there is no disagreement between the counterparties
- **Token** called an "æon" or "AE token“
  - Used to pay for **space** and **computation time**on the virtual machine


# Summary
- Blockchain networks have **scalability** and **performance** issues
  - Solved by faster consensus, offchain transactions, blockchain sharding, sidechains and post-blockchain ledger technologies
- **Payment channels**allow unlimited instant direct transactions
  - Powered by **Hashed Time-Locked Contracts (HTLC)**
  - **Payment networks**and **cross-chain transactions**
- **Sidechains** run parallel blockchains
  - Commit continuously their state to the main chain
- **Sharding**splits the chain and transactions into shards running in parallel
![](/assets/scaling-the-blockchain-networks-summary-01.png)


# Resources
- Payment channels explained: https://arxiv.org/pdf/1702.05812.pdf
- Scalability: https://www.oreilly.com/ideas/blockchain-scalability 
- Lighting Network: https://lightning.network/ 
- Off-chain transactions: https://blog.lightning.engineering/announcement/2017/11/16/ln-swap.html




