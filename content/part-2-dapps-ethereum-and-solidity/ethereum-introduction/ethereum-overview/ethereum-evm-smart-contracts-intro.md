# Overview of Ethereum, EVM and Smart Contracts

## Ethereum, Network Components, Ethers, Blocks, Transactions, Gas, Problems, Solutions


# Table of Contents
- Overview of the **Ethereum** Public Blockchain
  - Background, History, Releases
  - **Ethereum** vs. **Bitcoin**
  - The State-Machine behind **Ethereum**
  - Main Components of Ethereum System
  - What is **Ether**?
- Ethereum Problems: Scaling, Costs, …
- Ethereum Clients: **geth** and **Parity**
![](/assets/ethereum-overview-table-of-contents-01.png)
![](/assets/ethereum-overview-table-of-contents-02.png)


# The Ethereum Blockchain
- History, Architecture, Components 
![](/assets/ethereum-overview-the-ethereum-blockchain-01.png)


# What is Ethereum? 
- Ethereum – popular public blockchain network
  - Distributed computing platform with **smart contract**functionality
  - Open-source, public project
  - Provides a cryptocurrency coin – **“ether”**
- Ethereum **fork**: Ethereum vs. Ethereum Classic
  - Caused by the collapse of "**The DAO**" project
![](/assets/ethereum-overview-what-is-ethereum-01.png)


# Blockchain Definition
- Cryptographically secure
  - **Digital currency**- secured by complex mathematical algorithms
- Transactional singleton machine
  - Responsible for all the **transactions**
- With shared-state
  - State stored on this machine is **shared** and **open**
![](/assets/ethereum-overview-blockchain-definition-01.png)


# Ethereum vs Bitcoin
- Bitcoin vs. Ethereum
- **Founder**
- **Release Date**
- **Release Method**
- **Blockchain**
- **Usage**
- **Cryptocurrency Used**
- **Algorithm**
- **Blocks Time**
- **Mining**
- Bitcoin
- **Satoshi Nakamoto**
- **9 Jan 2008**
- **Genesis Block Mined**
- **Proof of Work**
- **Digital Currency**
- **Bitcoin(Satoshi)**
- **Sha256**
- **10 minutes**
- **ASIC miners**
- Ethereum
- **Vitalik Buterin**
- **30 July 2015**
- **Presale**
- **Proof of Work**
- **Currency/Smart Contracts**
- **Ether**
- **Ethash**
- **12-14 seconds**
- **GPUs**
![](/assets/ethereum-overview-ethereum-vs-bitcoin-01.png)
![](/assets/ethereum-overview-ethereum-vs-bitcoin-02.png)


# Ethereum History
- **Vitalik Buterin**
  - Cryptocurrency researcher & developer
  - Co-founder of **Bitcoin Magazine**
  - Learn more at: https://about.me/vitalik_buterin
- The Ethereum **whitepaper** (2013)
  - "A Next Generation Smart Contract & Decentralized Application Platform" by Vitalik Buterin – https://goo.gl/Xgdfgk
- **Ether sale ICO**(2014) raised 14M USD (~32K BTC)
- In 30 July 2015 the **main net**launched – etherscan.io/block/0
![](/assets/ethereum-overview-ethereum-history-01.png)




# Ethereum Blockchain Paradigm
- Transaction-based state machine
  - **Transition** to a new **state** by reading a series of **inputs**
- Ethereum **transactions** transit from one state to another state
![](/assets/ethereum-overview-ethereum-blockchain-paradigm-01.png)


<!-- # Ethereum Blockchain Paradigm -->
- Begins with a **“genesis state”**
- **Transaction** execution generates a **new state**
- The blockchain holds all states of the **Ethereum** network over the time – see https://etherscan.io/txs
- Genesis state
- State 2
- State 3
- State n


<!-- # Ethereum Blockchain Paradigm -->
- The **Ethereum global state**is **represented** by a **State Trie**
  - **Valid** **state transitions**are **captured** in each **block heade**r as a **Merkle-PATRICIA Trie Root**
- **Block 1**
- **Header**
- State root
- Trans. Root
- Receipts Root
- **Block 2**
- **Header**
- State root
- Trans. Root
- Receipts Root
<div class="fragment balloon" style="top:35.36%; left:101.47%; width:38.29%">**Merkle-PATRICIA** Trie Root</div>
<div class="fragment balloon" style="top:56.57%; left:101.47%; width:38.29%">The **State Root**(**global state**) is simply a **mapping** between **addresses and accounts**</div>
- **Create Account/Contract**
- **Change Balance**
- **State Transition**
- **New transaction output**
- **New transactions**


<!-- # Ethereum Blockchain Paradigm -->
- **Transactions** are grouped into “**blocks**”
  - Contains a series of **transactions**
  - Block is chained together with its previous **block**

```cs
Block 1






```

- **Header**
- Transactions
- **Block 2**
- **Header**
- Transactions
- **Block N**
- **Header**
- Transactions


<!-- # Ethereum Blockchain Paradigm -->
- To validate a transaction - must go through a validation process a.k.a. **mining**
  - Fastest **miner** adds **block** to the main **blockchain**
    - Rewarded with a certain amount of **Ethers**
  - Validating block – **“proof of work”**
![](/assets/ethereum-overview-ethereum-blockchain-paradigm-5-01.png)


# The Ethereum World State
- Explanation & Implementation
![](/assets/ethereum-overview-the-ethereum-world-state-01.png)


# Building Ethereum World State
- The **concept** of **Ethereum Account**plays a **fundamental** part on the **Ethereum Blockchain**
  - Both **contracts** and **normal** (external) **accounts** behave in **the same way**
<div class="fragment balloon" style="top:46.63%; left:1.61%; width:36.76%">How do we **build** a **valid** (simplified) **Ethereum State**?</div>
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**
<div class="fragment balloon" style="top:34.76%; left:90.91%; width:43.78%">We define this global state using 4 **sample** **accounts** and their **corresponding value**</div>
<div class="fragment balloon" style="top:64.85%; left:90.91%; width:45.39%">**Realistically**, accounts hold **a lot more** than **value**</div>


# Building Ethereum World State
- The **concept** of **Ethereum Account**plays a **fundamental** part on the **Ethereum Blockchain**
  - Both **contracts** and **normal** (external) **accounts** behave in **the same way**
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**
<div class="fragment balloon" style="top:46.63%; left:1.61%; width:36.76%">How do we **build**a **valid** (simplified) **Ethereum State**?</div>
<div class="fragment balloon" style="top:34.76%; left:90.91%; width:43.78%">We define this global state using 4 **sample** **accounts** and their **corresponding value**</div>
<div class="fragment balloon" style="top:64.85%; left:90.91%; width:45.39%">**Realistically**, accounts hold **a lot more** than **value**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**
<div class="fragment balloon" style="top:21.65%; left:37.21%; width:43.78%">Let’s try and **build** a **simple** **Ethereum World State**from the **mapping table** we have</div>
<div class="fragment balloon" style="top:50.56%; left:82.59%; width:43.78%">**Add** each **address** and its **corresponding account**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
<div class="fragment balloon" style="top:32.02%; left:76.32%; width:39.09%">We **add** the **first account** as a **Leaf Node**</div>
<div class="fragment balloon" style="top:32.82%; left:1.92%; width:40.11%">For **convenience** we **start** with the **state root**(**usually computed last**)</div>
- **Key**
- **a711355**
<div class="fragment balloon" style="top:57.06%; left:27.51%; width:30.71%">**Leaf Nodes**consist of a **Key**and a **Value**</div>
- **Value**
- **45.0ETH**


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
<div class="fragment balloon" style="top:32.02%; left:76.32%; width:39.09%">We **add** the **first account** as a **Leaf Node**</div>
<div class="fragment balloon" style="top:32.82%; left:1.92%; width:40.11%">For **convenience** we **start** with the **state root**(**usually computed last**)</div>
- **Key**
- **Value**
- **a711355**
- **45.0ETH**
<div class="fragment balloon" style="top:57.06%; left:27.51%; width:30.71%">**Leaf Nodes**consist of a **Key**and a **Value**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
<div class="fragment balloon" style="top:32.02%; left:76.32%; width:39.09%">We **add** the **first account** as a **Leaf Node**</div>
<div class="fragment balloon" style="top:32.82%; left:1.92%; width:40.11%">For **convenience** we **start** with the **state root**(**usually computed last**)</div>
- **Key**
- **Value**
- **a711355**
- **45.0ETH**
<div class="fragment balloon" style="top:57.06%; left:27.51%; width:30.71%">**Leaf Nodes**consist of a **Key**and a **Value**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
<div class="fragment balloon" style="top:32.02%; left:76.32%; width:39.09%">We **add** the **first account** as a **Leaf Node**</div>
<div class="fragment balloon" style="top:32.82%; left:1.92%; width:40.11%">For **convenience** we **start** with the **state root**(**usually computed last**)</div>
- **Key**
- **Value**
- **a711355**
- **45.0ETH**
<div class="fragment balloon" style="top:57.06%; left:27.51%; width:30.71%">**Leaf Nodes**consist of a **Key**and a **Value**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- **Key**
- **Value**
- **a711355**
- **45.0ETH**
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
<div class="fragment balloon" style="top:36.63%; left:91.10%; width:41.11%">We **add** the **second** **account** to the **Trie**</div>
<div class="fragment balloon" style="top:40.73%; left:36.03%; width:48.58%">**Notice** that the **second** **address** starts with the same **byte** **0xa7**. Thus, we can **group** **both** accounts.</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- **Key**
- **Value**
- **a711355**
- **45.0ETH**
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
<div class="fragment balloon" style="top:36.63%; left:91.10%; width:41.11%">We **add** the **second** **account** to the **Trie**</div>
<div class="fragment balloon" style="top:40.73%; left:36.03%; width:48.58%">**Notice** that the **second** **address** starts with the same **byte** **0xa7**. Thus, we can **group** **both** accounts.</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
<div class="fragment balloon" style="top:36.63%; left:91.10%; width:41.11%">We **add** the **second** **account** to the **Trie**</div>
- **Key**
- **a7**
<div class="fragment balloon" style="top:34.51%; left:27.14%; width:32.67%">**Extension** Nodes **combine** addresses with **same** **prefixes**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
<div class="fragment balloon" style="top:36.63%; left:91.10%; width:41.11%">We **ADD** the **SECOND** **Account** to the **Trie**</div>
- **Key**
- **Next**
- **a7**
<div class="fragment balloon" style="top:34.51%; left:27.14%; width:32.67%">**Extension** Nodes **combine** addresses with **same** **prefixes**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
<div class="fragment balloon" style="top:36.63%; left:91.10%; width:41.11%">We **add** the **second** **account** to the **Trie**</div>
- **Key**
- **Next**
- **a7**
<div class="fragment balloon" style="top:34.51%; left:27.14%; width:32.67%">**Extension** Nodes **combine** addresses with **same** **prefixes**</div>
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
<div class="fragment balloon" style="top:34.51%; left:2.26%; width:23.13%">This is a **Branching** Node</div>
- **Key**
- **Value**
- **1355**
- **45.0ETH**
- **Key**
- **Value**
- **d337**
- **1.00WEI**


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
<div class="fragment balloon" style="top:36.63%; left:91.10%; width:41.11%">We **add** the **second** **account** to the **Trie**</div>
- **Key**
- **Next**
- **a7**
<div class="fragment balloon" style="top:34.51%; left:27.14%; width:32.67%">**Extension** Nodes **combine** addresses with **same** **prefixes**</div>
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
<div class="fragment balloon" style="top:34.51%; left:2.26%; width:23.13%">This is a **Branching** Node</div>
- **Key**
- **Value**
- **1355**
- **45.0ETH**
- **Key**
- **Value**
- **d337**
- **1.00WEI**


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- **Key**
- **Next**
- **a7**
<div class="fragment balloon" style="top:34.51%; left:27.14%; width:32.67%">**Extension** Nodes **combine** addresses with **same** **prefixes**</div>
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
<div class="fragment balloon" style="top:34.51%; left:2.26%; width:23.13%">This is a **Branching** Node</div>
- **Key**
- **Value**
- **1355**
- **45.0ETH**
- **Key**
- **Value**
- **d337**
- **1.00WEI**
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- **Key**
- **Value**
- **9365**
- **1.1ETH**
<div class="fragment balloon" style="top:42.12%; left:92.09%; width:41.11%">We **add** the **third** **account** to the **Trie**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- **Key**
- **Next**
- **a7**
<div class="fragment balloon" style="top:34.51%; left:27.14%; width:32.67%">**Extension** Nodes **combine** addresses with **same** **prefixes**</div>
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
<div class="fragment balloon" style="top:34.51%; left:2.26%; width:23.13%">This is a **Branching** Node</div>
- **Key**
- **Value**
- **1355**
- **45.0ETH**
- **Key**
- **Value**
- **d337**
- **1.00WEI**
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- **Key**
- **Value**
- **9365**
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**
<div class="fragment balloon" style="top:42.12%; left:92.09%; width:41.11%">We **add** the **third** **account** to the **Trie**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- **Key**
- **Next**
- **a7**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**
<div class="fragment balloon" style="top:49.49%; left:98.28%; width:41.11%">We **add** the **final** **account** to the **Trie**</div>
<div class="fragment balloon" style="top:32.41%; left:51.51%; width:36.17%">Many **accounts** share **similar** **addresses**. **Thus**, we need to **rearrange**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- **Key**
- **Next**
- **a7**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**
<div class="fragment balloon" style="top:49.49%; left:98.28%; width:41.11%">We **add** the **final** **account** to the **Trie**</div>
<div class="fragment balloon" style="top:32.41%; left:51.51%; width:36.17%">Many **accounts** share **similar** **addresses**. **Thus**, we need to **rearrange**</div>


# Building Ethereum World State
- a
- 7
- 1
- 1
- 3
- 5
- 5
- **45.0ETH**
- State Root
- a
- 7
- 7
- d
- 3
- 3
- 7
- **1.00WEI**
- **Key**
- **Next**
- **a7**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- a
- 7
- f
- 9
- 3
- 6
- 5
- **1.1ETH**
- a
- 7
- 7
- d
- 3
- 9
- 7
- **0.12ETH**


# Building Ethereum World State
- State Root
- **Key**
- **Next**
- **a7**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- **Key**
- **Next**
- **d3**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- **Key**
- **Value**
- **7**
- **1.00WEI**
- **Key**
- **Value**
- **1355**
- **45.0ETH**
- **Key**
- **Value**
- **7**
- **0.12ETH**
- **Key**
- **Value**
- **9365**
- **1.1ETH**

```cs
Account 1
```


```cs
Account 2
```


```cs
Account 3
```


```cs
Account 4
```



# Searching for an Ethereum Account
- State Root
- **Key**
- **Next**
- **a7**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- **Key**
- **Next**
- **d3**
- **Value**
- 0
- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- a
- b
- c
- d
- e
- f
- **Key**
- **Value**
- **7**
- **1.00WEI**
- **Key**
- **Value**
- **1355**
- **45.0ETH**
- **Key**
- **Value**
- **7**
- **0.12ETH**
- **Key**
- **Value**
- **9365**
- **1.1ETH**

```cs
Account 1
```


```cs
Account 2
```


```cs
Account 3
```


```cs
Account 4
```

<div class="fragment balloon" style="top:12.97%; left:92.59%; width:41.11%">We **want** to **find** the account for **address** **a77d397** </div>


# Other components of Ethereum
- GHOST Protocol, EVM, Ether…
![](/assets/ethereum-overview-other-components-of-ethereum-01.png)


# The "GHOST" Protocol
- **GHOST** == **G**reedy **H**eaviest **O**bserved **S**ub**T**ree
  - Blocks can reference **multiple predecessors**
  - Cumulative difficulty calculation **includes** “uncles”
  - Blocks that ended up **not** on main chain **still contribute to security**
- In reality, **simplified version**is used
  - Uncles get **some** subsidy
    - But their **transactions don’t count**, and they **don’t get fees**
  - Removes incentive to **continue a fork**


# Main Components of Ethereum System
- Nodes – http://ethernodes.org
- Accounts – https://etherscan.io/accounts
- Blocks – https://etherscan.io/blocks
- Transactions – https://etherscan.io/txs
  - Transaction execution engine
  - Gas, gas price and fees
- State – https://ethstats.net
- Mining & Proof-of-Work
![](/assets/ethereum-overview-main-components-of-ethereum-system-01.png)


# The Ethereum Virtual Machine
- Simple but powerful **Turing-complete** 256-bit **Virtual Machine**
- Accessible from any Ethereum Node in the network
- Crucial role in the consensus engine of the **Ethereum** system
- **Guarantees** and fully **determines**an outcome of an executed code
![](/assets/ethereum-overview-the-ethereum-virtual-machine-01.png)


# EVM 
- EVM is **stack-based VM**
  - Uses **bytecode** to encode the instructions
- Developers use **Solidity**
  - Compiled to bytecode
- EVM **assembly code** can also be used
  - For advanced developers
![](/assets/ethereum-overview-evm-01.png)


# What is Ether?
- **Ether** == value coin of the **Ethereum** blockchain
  - Symbol – **ETH**
  - Traded on **cryptocurrency** exchanges
- Pay in ETH for:
  - Transaction **fees**
  - Computational services (**gas** toexecute smart contract's code)
- Market price: coinmarketcap.com/currencies/ethereum/
![](/assets/ethereum-overview-what-is-ether-01.png)


# ENS
- Ethereum Naming System is the **DNS for the Ethereum world**
- Мaps human-readable name to Ethereum contract or wallet address
- Example: **google.com → 146.115.22.177**
- Example from Ethereum world: **mywallet.eth** **&rarr; 0x80C013d980aB049471c88E1603…**
- Based on a **smart contract**
- https://ens.domains 
![](/assets/ethereum-overview-ens-01.png)


# Ethereum Problems: Scalability
- Processing around **10 - 15 transactions/second**
  - VISA processes around **2000 transactions/second**
- Due to the manner in which transactions are validated 
  - Maintain a copy of the blockchain 
  - Process each transaction made on it
![](/assets/ethereum-overview-ethereum-problems-scalability-01.png)


# How will Ethereum Scale?
- Sharding
  - Breaks **database** into pieces 
  - Puts each part on a **different server**
  - Move away from **“full” nodes**
  - Process isn't exactly **trustless**
- Off-chain transactions
  - Raiden: payment network, made on **off-chain** micropayment channels
  - Lifting from the underlying **blockchain**
  - Can be back to the blockchain anytime 
![](/assets/ethereum-overview-how-will-ethereum-scale-01.png)


# Ethereum Problems: Transaction Costs
- Transactions in Ethereum can be **very expensive**
    - **cost = gasConsumed * gasPrice**
    - E.g. 210 000 gas * 20 GWei/gas = 0.0042 ETH * 600 USD/ETH = 2.52 USD per transaction
    - **Gas price** == how much **Ether** the user is willing to pay per **gas**
![](/assets/ethereum-overview-ethereum-problems-transaction-costs-01.png)


# Ethereum Problems: Oracles Problem
- In blockchain networks an **oracle** is provider of data
  - Gives to **smart contracts**answers to questions about the world
  - E.g. what is the price of BTC or what is the temperature in Sofia
- Holds the power to control what the **smart contract**does 
- Centralized vs. decentralized oracles
- In search of the perfect oracle
  - **Augur**– **http://www.augur.net** 
  - **Gnosis** – **https://gnosis.pm** 
![](/assets/ethereum-overview-ethereum-problems-oracles-problem-01.png)
![](/assets/ethereum-overview-ethereum-problems-oracles-problem-02.png)


# Ethereum Useful Resources
- Ethereum Project Website 
  - https://www.ethereum.org 
- Ethereum Block Explorer
  - https://etherscan.io
- Ethereum Stats
  - https://ethstats.net
- Ethereum Cryptocurrency 
  - https://coinmarketcap.com/currencies/ethereum/ 
![](/assets/ethereum-overview-ethereum-useful-resources-01.png)
![](/assets/ethereum-overview-ethereum-useful-resources-02.png)
![](/assets/ethereum-overview-ethereum-useful-resources-03.png)
![](/assets/ethereum-overview-ethereum-useful-resources-04.png)


# Geth and Mist – Official Ethereum Clients
- **Ethereum client**
  - A software designed to interact with the Ethereum network
  - Might implement a **wallet** to keep addresses + private keys
  - Example Ethereum clients: **geth**, **Parity**, **pyethapp**
- **Geth** – https://geth.ethereum.org  
  - Console-based Ethereum client, node and wallet
- **Mist**– **https://github.com/ethereum/mist**
  - GUI for the Geth client
  - Browse and use DApps on the Ethereum network


<!-- #  Blockchain Nodes – Go-Ethereum (Ge -->
- The official Ethereum node software, written in Go
- Connects to other **clients / nodes**
- Downloads a copy of the entire blockchain (takes time)
- **Keep its copy**of the blockchain up to date
- **Mine** blocks 
- **Send** transactions 
- **Validate** the transactions 
- **Execute** the transactions
![](/assets/ethereum-overview-blockchain-nodes-go-ethereum-geth-01.png)
![](/assets/ethereum-overview-blockchain-nodes-go-ethereum-geth-02.png)


<!-- #  Blockchain Nodes – Go-Ethereum (Geth) -->
- **geth console**
  - Command line tool 
  - Starts a **local node**/ connect to other nodes
  - Create and manage **accounts**
  - **Query** the blockchain
  - Sign and submit **transactions**
  - **https://geth.ethereum.org/downloads** 
![](/assets/ethereum-overview-blockchain-nodes-go-ethereum-geth-2-01.png)


# Running geth
- Run geth on Mainnet
- On testnet with command line
- Manage wallets and accounts                       e.g. 
- Manage mining functionality                 e.g. 
- Essential information regarding the node           e.g.
- Manage local node                  e.g. 
- Check your etherbase account balance
![](/assets/ethereum-overview-running-geth-01.png)


<!-- # [Demo -->
- Playing with Geth
![](/assets/ethereum-overview-demo-01.png)


# Exercise
- Playing with Geth and Mist
![](/assets/ethereum-overview-exercise-01.png)


# The "Parity" Ethereum Client
- Parity == implementation of the Ethereum protocol
  - Written in **Rust**
- It is an alternative Ethereum client, used to run a node
- Maintained by a company called**Parity Inc.**(by **Gavin Wood**)
- Anyone can implement the client software and join the Ethereum network
- https://www.parity.io 
![](/assets/ethereum-overview-the-parity-ethereum-client-01.png)


<!-- # [Demo -->
- Playing with Parity
![](/assets/ethereum-overview-demo-01.png)


# Summary
- Ethereum is **blockchain-based**distributed computing platform 
  - Ethereum’s creator is **Vitalik Buterin** and few others
  - **Smart contracts**, running in the EVM, written in Solidity
  - **Ether** is value coin of the **Ethereum** blockchain
  - **Geth** and **Mist** are the official console-based and GUI clients
- Major problems at the Ethereum blockchain
  - **Scalability**, **performance**and **transaction costs**
  - Possible solutions: **sidechains** and **off-chain transactions**
![](/assets/ethereum-overview-summary-01.png)


# Resources
- What is Ethereum: https://coindesk.com/information/what-is-ethereum/ 
- How Ethereum Works: https://medium.com/@preethikasireddy/how-does-ethereum-work-anyway-22d1df506369 
- How to Use Ethereum: https://www.coindesk.com/information/how-to-use-ethereum/ 
- What is Ether: https://www.coindesk.com/information/what-is-ether-ethereum-cryptocurrency/ 
- How will Ethereum Scale: https://www.coindesk.com/information/will-ethereum-scale/ 
- Scalability: https://www.mycryptopedia.com/sharding-the-solution-to-ethereums-scalability-problem/ 
- The Oracle Problem: https://ether.direct/2017/07/15/the-oracle-problem/ 




