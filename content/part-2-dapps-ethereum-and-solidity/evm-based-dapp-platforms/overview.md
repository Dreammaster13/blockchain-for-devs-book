# Chapter 2.10. EVM-Based Smart Contract and DApp Platforms

# Notable DApp Platforms
## RSK, Qtum, POA Network, NEO, EOS, Cardano, TRON, Aeternity, Tezos, Steem, Quorum

# Table of Contents
- RSK
- POA Network
- NEO
- EOS
- Cardano
- Aeternity
- Tezos
- Steem + SteemDB + SteemData
- Quorum
![](/assets/notable-dapp-platforms-table-of-contents-01.png)
![](/assets/notable-dapp-platforms-table-of-contents-02.png)
![](/assets/notable-dapp-platforms-table-of-contents-03.png)


# Web App Architecture

```cs
PHP, NodeJS,Python
```


```cs
Normal Server or Cloud
Provider
```


```cs
HTML, CSS, JavaScript
```


```cs
+ Frameworks
```

![](/assets/notable-dapp-platforms-web-app-architecture-01.png)
![](/assets/notable-dapp-platforms-web-app-architecture-02.png)
![](/assets/notable-dapp-platforms-web-app-architecture-03.png)


# dApp Architecture

```cs
HTML, CSS, JavaScript
```


```cs
+ Frameworks
```


```cs
Solidity for Ethereum
```


```cs
Other smart-contract 
platforms
```

![](/assets/notable-dapp-platforms-dapp-architecture-01.png)
![](/assets/notable-dapp-platforms-dapp-architecture-02.png)


# What are Decentralized Apps (DApps)?
  - Software applications, running in a decentralized network
  - **Common features of DApps**
  - Open source / public
  - Decentralized 
  - Incentivized (tokens / rewards)
  - P2P protocols / consensus
![](/assets/notable-dapp-platforms-what-are-decentralized-apps-dapps-01.png)


# Decentralized App Platforms
![](/assets/notable-dapp-platforms-decentralized-app-platforms-01.png)


# Rootstock
![](/assets/notable-dapp-platforms-rootstock-01.png)


# RSK
- **Sidechain** to **Bitcoin** network using **two-way peg**
- BTC are locked in Bitcoin and the same amount of RTC are unlocked in RSK
- **Turing-complete** resource-accounted deterministic virtual machine for Smart Contracts 
- **RVM** (RSK Virtual Machine) – independent, compatible with **EVM** (opcode level)
  - allows Ethereum contracts to run with **Bitcoin**

```cs
www.rsk.co
```



# RSK #2
- Dynamic Hybrid Merged mining / Federation
  - DECOR+ block reward sharing protocol
  - **GHOST** rules

```cs
www.rsk.co
```



# Qtum
![](/assets/notable-dapp-platforms-qtum-01.png)


# Qtum
- Combines Bitcoin’s **UTXO model** and **EVM smart contracts**
  - Special **Bitcoin Script opcodes**, like “give this data to the EVM”
  - Special **consensus rules**for things like gas refund transactions
  - **Adapter layer**that translates between UTXOs and accounts
    - Most Ethereum smart contracts should run with **minimal or no modification**
  - Aims to achieve **better scaling**than Ethereum’s account model

```cs
https://qtum.org/
```



# Qtum
- In the future, possible to add **other VMs** and **innovations from the UTXO model** (e.g. Zcash-style anonymous transactions)
- **Proof-of-Stake**
- Modules for oracles and things like KYC/AML


# POA Network
![](/assets/notable-dapp-platforms-poa-network-01.png)


# POA Network
- Inspired by Ethereum’s **Kovan** Testnet
  - Which in turn is a response to a **spam attack** on **Ropsten** Testnet
- **Proof-of-Authority**
  - Validators selected **manually**
  - Public notaries holding a license in the U.S.
- **In essence, a permissioned public blockchain**
- Compatible with **Ethereum** and **Solidity smart contracts**
- Network forks as **legal contracts**

```cs
https://poa.network
```



# NEO
![](/assets/notable-dapp-platforms-neo-01.png)


# NEO
- Introduces **Smart Economy**(Digital Assets + Digital Identity + Smart Contracts)
  - Real assets can be digitized, traded using rules in Smart Contracts, knowing with who using Digital Identity
- Native tokens
  - **NEO** – represents the right to manage the network + governance
  - **GAS** – fuel token of NEO network resource control
- Consensus Algorithm – Delegated Byzantine Fault Tolerance (**dBFT**)

```cs
https://neo.org
```



# NEO #2
- Has it own lightweight **NeoVM**– uses JIT (**just-in-time**) compilation
- Smart Contracts in **C#**, **Java**and **Python**
- **Cross-chain**interoperability agreement – NeoX 
- **NeoFS**– Distributed Storage Protocol
- **NeoQS**– Anti-quantum cryptography mechanism




# EOS
![](/assets/notable-dapp-platforms-eos-01.png)


# EOS
- From the creators of **Steem** and **BitShares**
- Focus on **scalability**
  - **Sharding**
  - Application-defined **filtering**(applications can ignore events they don’t care about)
- **Delegated Proof-of-Stake**
- **No TX fees**, but available resource **determined by stake**
  - Possible for **receiver** to “pay”, not just sender

```cs
https://eos.io/
```



# EOS
- Resource usage determined **subjectively** by nodes and network consensus
  - Instead of fixed price per instruction
  - Provides opportunities for **low-level optimizations**
- **VM independent**, but initially **Web Assembly (through C++)**


# EOS

```cs
namespace Oasis {
   using namespace eosio;
   using std::string;
   class Players : public contract {
        using contract::contract;
        public:
            //@abi action
       void add(const account_name account, string& username, uint64_t level) { …… }
            //@abi action
       void update(const account_name account) { …… }
    };
}
```



# Cardano
![](/assets/notable-dapp-platforms-cardano-01.png)


# Cardano
- **Proof-of-Stake**
  - Extensive **security research** on the protocol
  - Time divided in **epochs** and **slots**
    - A community of leaders voted for entire epoch
    - …but subdivided in slots, for faster “block time”
- Implemented in **Haskell**
- **Software updates** announced **on-chain**
  - After **voting** by stakeholders
- **Smart contracts** language (Plutus) inspired by **Haskell**

```cs
www.cardano.org
```



# Tron
![](/assets/notable-dapp-platforms-tron-01.png)


# Tron
- **Blogging** platform (with usernames and messaging)
- **File storage** like in BitTorrent
- **Smart contracts** written in any language
- **UTXO transaction model**, like in Bitcoin
- **Proof-of-Stake**
- **Lamport signatures**instead of ECDSA (quantum resistance)
- Focused on the **entertainment industry**
- Whitepaper generally of **low quality**

```cs
https://tron.network
```



# aeternity
![](/assets/notable-dapp-platforms-aeternity-01.png)


# Æternity
- Instead of Turing machine → **Oracle machine**
  - Can compute **non-computable functions**
    - E.g. which team won a football game
  - Integrates decentralized **oracle consensus** as part of network consensus
    - Agrees not only on internal state, but also **external (world) state**
    - **More efficient** than doing this as a second layer, with smart contracts
- Implemented in Erlang and Elixir

```cs
https://aeternity.com
```



# Æternity
- Implemented in Erlang and Elixir
- Focus on **state channels**, for off-chain computation
- OCaml-based **smart contracts** language
- Hybrid **Proof-of-Work** and **Proof-of-Stake**
- **Governance by integrated voting and prediction markets**


# Æternity Solidity Example

```cs
contract SimpleStorage {
   uint private storedData;
   function set(uint x) public { storedData = x;}
   function get() view public returns (uint) {
      return storedData; }
}
```



# Æternity Sofia Example

```cs
contract FundMe =
type state = { contributions : map(address, uint),
total : uint,
beneficiary : address,
deadline : uint,
goal : uint }
//define require method, second parameter is the error msg
private function require(b : bool, err : string) =
if(!b) abort(err)
public function init(beneficiary, deadline, goal) : state =
{ contributions = Map.empty,
beneficiary = beneficiary,
deadline = deadline,total = 0, goal = goal }
```



# Æternity Varna Example

```cs
function buy_tokens(value: aeons) : void
     var amount : integer = (value / oracle("GameTokenPrice", "price"))
     if owner.tokens."GameTokens" > amount then
        caller.tokens."GameTokens" += amount
        owner.tokens."GameTokens" -= amount
        owner.balance += value
     end
 end
```



# Tezos
![](/assets/notable-dapp-platforms-tezos-01.png)


# Tezos
- **“Meta-blockchain”**
  - A general interface that can be used to implement **any blockchain**
  - Changes to the actual protocols by integrated **voting system**
- **Proof-of-Stake**
- Implemented in **OCaml**
- Smart contracts in **Liquidity**
  - OCaml-inspired
  - Focus on correctness and **formal verification**
  - **http://www.liquidity-lang.org/**

```cs
https://tezos.com
```



# Steem
![](/assets/notable-dapp-platforms-steem-01.png)


# Steem
- Runs a **popular blogging platform**, SteemIt
- Extremely **high performance**
  - Has handled **2.5M transactions in one day** in practice
  - Has tested at **tens of times that**
- High **resource requirements** for nodes (>128GB RAM)

```cs
https://steem.io
```



# Steem
- **Complex economic model**, with multiple different tokens
  - Network consensus used to determine exchange rates, so that e.g. SBD is fixed to USD
  - Backed by user content
- **Delegated Proof-of-Stake**
- There exists **adapter software**that lets you use **SQL queries**


# Quorum
![](/assets/notable-dapp-platforms-quorum-01.png)


# Quorum
- Ethereum based permissioned blockchain made by **JPMorgan**
  - Permission & Governance
  - Performance & Throughput
  - Privacy 
- **Configurable Consensus**
  - QuorumChain – **POS**
  - Raft – **Leader Election**
  - Istanbul - **BFT**


# Quorum
- Minimal **geth** client changes
- **Private** smart contracts
- Public and private transactions
  - **Separated Patricia tree**for public and private transactions
- There is gas, but gas cost **nothing**
- Part of **E**nterprise **E**thereum **A**lliance
- Open source
- Implemented in **GOLANG**


# Summary
- DApps → an evolution of private-server and cloud-based apps
- Censorship resistance, public ownership of data
- Many different platforms for running DApps
- Proof-of-Stake and variants common in newer platforms
![](/assets/notable-dapp-platforms-summary-01.png)


# Resources
- Quorum
  - https://github.com/ethereum/EIPs/issues/650
  - https://www.youtube.com/watch?v=VRAyzt7B76I
  - https://github.com/jpmorganchase/quorum/wiki
![](/assets/notable-dapp-platforms-resources-01.png)
