# Web3 API, MetaMask and Client-Side Interaction with Ethereum

## Accessing the Ethereum Networkfrom JavaScript through JSON-RPC

# Table of Contents
- What is Web3?
- Installing Web3
- Using Web3 API
- Infura API 
- Ethereum JSON-RPC providers
- MetaMask
- Injected Web3
![](/assets/web3-and-metamask-table-of-contents-01.png)
![](/assets/web3-and-metamask-table-of-contents-02.png)


# The Web3 API
- Interacting with the Ethereum Network
![](/assets/web3-and-metamask-the-web3-api-01.png)


# The Ethereum JavaScript API – Web3.js
- Web3.js – a JavaScript **library to**interact with Ethereum nodes


# Installing Web3 in Windows
- First install "**Windows Build Tools**" for Node.js
  - https://www.npmjs.com/package/windows-build-tools
  - Run as Administrator
- Then, configure the VC++ target
- Finally, install the "web3" package


# Using Web3 API
- Creating an instance of **web3** using **HTTP** provider
- Provides the **Ethereum** blockchain related methods
- Getting the balance of account


<!-- # Using Web3 API -->
- Get the account for mining rewards (the default account)
- Get all accounts
- Create contract object
- Deploy contract


<!-- # Using Web3 API -->
- Invoking functions from existing smart contract


# Infura API
- **Infura** provides a gateway to the Ethereum blockchain
  - Signup and get a free **JSON RPC endpoint**to the Ethereum Mainnet, Ropsten, Kovan, Rinkeby, and other networks
  - Instead of running a local Ethereum node, just use **Infura.io**


# Ethereum JSON-RPC Providers
- Infura, MyEtherAPI, Own Ethereum Node
![](/assets/web3-and-metamask-ethereum-json-rpc-providers-01.png)


# Ethereum JSON-RPC Endpoints
- How to access the Ethereum network?
  - You need a **JSON-RPC provider**to connect the Web3 API
- Run your own Ethereum node or node-as-a-service
  - Use **geth**, **Parity** or https://quiknode.io 
- **Infura**
  - А free Ethereum JSON-RPC and IPFS endpoints (by ConsenSys)
- **MyEtherAPI**
  - A free Ethereum JSON-RPC provider (by MyEtherWallet)


# Infura API – Live Example

```cs
let Web3 = require('web3');
let web3 = new Web3('https://ropsten.infura.io/z0NBZ7w5VCWFt9qjFUVk');
const contractAddress = '0x32d2f901d6b4b3473cb7aa2044b80216cf30b458';
const contractABI = […];

let contract = new web3.eth.contract(contractABI, contractAddress);
contract.methods.add('random hash').call().then(txHash => {
   console.log('Transaction hash: ', txHash) });
contract.methods.verify('random hash').call().then(retval => {
   console.log('Is valid?', retval); }); 
```



# MyEtherAPI
- **MyEtherAPI** provides a free JSON RPC endpoint to Ethereum Mainnet and Ropsten Тestnet
  - https://www.myetherapi.com
- Example:

```cs
let web3 = new Web3();
web3.setProvider(new web3.providers.HttpProvider(  'https://api.myetherapi.com/rop'));
web3.eth.getBalance("0x7cB57B5A97eAbe94205C07890BE4c1aD31E486A8").then(console.log);
```



# MetaMask
- In-Browser Ethereum Wallet + Web3 Provider
![](/assets/web3-and-metamask-metamask-01.png)
![](/assets/web3-and-metamask-metamask-02.png)


# What is MetaMask?
- Chrome / Firefox plugin
  - https://metamask.io 
- Install MetaMask and it **automatically connects**to the Ethereum nodes
- Used to **interact** with the Ethereum node
- **Host a number of nodes**so you don’t have to
![](/assets/web3-and-metamask-what-is-metamask-01.png)


# Installing MetaMask
![](/assets/web3-and-metamask-installing-metamask-01.png)


# Install and Configure MetaMask
![](/assets/web3-and-metamask-install-and-configure-metamask-01.png)
![](/assets/web3-and-metamask-install-and-configure-metamask-02.png)
![](/assets/web3-and-metamask-install-and-configure-metamask-03.png)
![](/assets/web3-and-metamask-install-and-configure-metamask-04.png)


# Configure MetaMask
- Create and Import Accounts
- Export private key from account
![](/assets/web3-and-metamask-configure-metamask-01.png)
![](/assets/web3-and-metamask-configure-metamask-02.png)
![](/assets/web3-and-metamask-configure-metamask-03.png)
![](/assets/web3-and-metamask-configure-metamask-04.png)


# Add Existing Token
![](/assets/web3-and-metamask-add-existing-token-01.png)
![](/assets/web3-and-metamask-add-existing-token-02.png)
![](/assets/web3-and-metamask-add-existing-token-03.png)


# Using Injected Web3.js in the Browser
- In the Web browser we should first check for **existing Web3 API**object, injected by MetaMask






<!-- # Signing and Sending Transactions -->
- Calling MetaMask
- Returns transaction hash
![](/assets/web3-and-metamask-signing-and-sending-transactions-2-01.png)


# Verifying a Certificate using Injected Web3
![](/assets/web3-and-metamask-verifying-a-certificate-using-injected-web3-01.png)


# Exercise: Decentralized Document Registry DApp
- Using Ethereum, Solidity, Web3 and MetaMask
![](/assets/web3-and-metamask-exercise-decentralized-document-registry-dapp-01.png)


# Exercise: Casino
- Ethereum, Truffle, React, Web3, IPFS, MetaМask
![](/assets/web3-and-metamask-exercise-casino-01.png)


# Summary
- Web3 – JavaScript library interacting with the Ethereum Nodes
- Web3 API
- **Infura** provides a gateway to the Ethereum blockchain
- Ethereum JSON-RPC Endpoints
- MetaMask Browser Extension
- Injected Web3 in Browser
![](/assets/web3-and-metamask-summary-01.png)
