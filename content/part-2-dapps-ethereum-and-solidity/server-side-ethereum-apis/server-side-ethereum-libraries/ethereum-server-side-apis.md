# Server-Side Ethereum APIs: Web3.js, Web3j, Web3.py, Nethereum, Ethers.js

## Web3.js, Ethers.js, Nethereum, Web3j, Web3py

# Table of Contents
- Solc-js
- Web3.js
- ethers.js
- Nethereum
- Web3j
- Web3.py
![](/assets/server-side-ethereum-libraries-table-of-contents-01.png)


# Solc-js
- JavaScript bindings for the Solidity Compiler
- Compile a contract using command line tool
- Generates
![](/assets/server-side-ethereum-libraries-solc-js-01.png)
![](/assets/server-side-ethereum-libraries-solc-js-02.png)
![](/assets/server-side-ethereum-libraries-solc-js-03.png)


<!-- # Solc-js -->
- As dev dependency
- Compile a contract in JS

```cs
let contractStr = `contract SimpleStorage {
   uint private storedData;
   function set(uint x) public { storedData = x;}
   function get() view public returns (uint) {
      return storedData; }
}`;
let output = solc.compile(contractStr);
```



# Compile Contract Result

```cs
{ assembly: {…},
  bytecode: '608060405234801561…',
  functionHashes: { 'get()': '6d4ce63c'…},
  gasEstimates: {…},
  interface:      '[{"constant":false,"inputs":[{…}]…},{"constant":…}…],
  metadata: '{"compiler":{"version":"0.4.24…","language":…}',
  opcodes: 'PUSH1 0x80 PUSH1 0x40 MSTORE CALLVALUE DUP1 ISZERO…',
  runtimeBytecode: '6080604052600436106049576000357c0100…',
  srcmap: '26:190:0…',
  srcMapRuntime: '26:190:0:…'
}
```



# Server-Side Ethereum Libraries

```cs
Web3.js, Ethers.js, Nethereum, Web3j, Web3py
```

![](/assets/server-side-ethereum-libraries-server-side-ethereum-libraries-01.png)


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
  - Signup and get a free **JSON RPC endpoint**to the Ethereum Mainnet, Ropsten, Kovan, Rinkeby and other networks
  - Instead of running a local Ethereum node, just use **Infura.io**


# Exercise: Smart Contracts Web3 and Infura
- Using Web3.js and Infura
![](/assets/server-side-ethereum-libraries-exercise-smart-contracts-web3-and-infura-01.png)


# ethers.js
- Feature-Complete library for Ethereum applications in JavaScript
- Web3 **alternative**
- Separation of concerns – key management and state
  - ethers.**Wallet** – holds keys, signs transactions
  - ethers.**providers** – connection to the Ethereum network, checking states and sending transactions


# Using ethers.js
- Get a provider to an Ethereum blockchain (e.g. Ropsten)
- Wait for transaction to be mined
- Create a Wallet instance for a particular chain 
- Get the **balance** of the address


# Using ethers.js – Contracts 
- Deploy a Contract
- Create a Contract Instance


# Interact with Contracts
<div class="fragment balloon" style="top:21.10%; left:72.27%; width:39.17%">Contract method name</div>
- **ArrayOfFacts**– simple Contract storing facts on the Blockchain
- **Add a Fact**to a contract
- **Read** **a Fact**from a contract


# Exercise: Smart Contractsethers.js
- Using ethers.js and Infura
![](/assets/server-side-ethereum-libraries-exercise-smart-contractsethers-js-01.png)


# Nethereum
- **.NET**integration library for Ethereum
- NuGetPackages
  - Web3
  - Contracts 
- Creating an **Account** from a private key
- Creating an instance of **web3** using **HTTP** provider


# Nethereum – Interact with Contracts
- Create a instance of an existing contract
- Send Transaction – Set contract stored data
<div class="fragment balloon" style="top:40.23%; left:99.60%; width:39.17%">Contract method name</div>


<!-- # Nethereum – Interact with Contracts -->
- Read from a contract
- Get Transaction Hash and do not wait to be mined
<div class="fragment balloon" style="top:10.41%; left:88.30%; width:47.77%">Contract method return type</div>


# Exercise: Smart Contracts
- Using Nethereum and Infura
![](/assets/server-side-ethereum-libraries-exercise-smart-contracts-01.png)


# Web3j
- **Java** and **Android** library for integration with Ethereum
- Creates Contract **wrappers** from native Java code
- Web3j Command Line Tools to **generate** wrapper code
- Maven dependency
![](/assets/server-side-ethereum-libraries-web3j-01.png)


# Using Web3j
- Creating an instance of **web3** using **HTTP** provider
- Load credentials by private key
- Deploy a contract


# Web3j – Invoke Contract Methods
- Load the Contract from an address
- Write to the contract, wait until is mined
- Read from a contract
<div class="fragment balloon" style="top:37.39%; left:99.60%; width:39.17%">Contract method name</div>


# Exercise: Smart ContractsWeb3j
- Using Web3j and Infura
![](/assets/server-side-ethereum-libraries-exercise-smart-contractsweb3j-01.png)


# Web3.py
- Python library for interaction with Ethereum
- API derived from Web3.js
- Very familiar to Web3.js
- Install package
- Import in a project


# Web3.py API
- Creating an instance of **web3** using **HTTP** provider
- Create a Contract Instance


# Web3.py API – Invoke Contract Methods
- **ArrayOfFacts**– simple Contract storing facts on the Blockchain
- **Add**a Fact to Contract
- Get Total Facts from the Contract


# Exercise: Smart ContractsWeb3.py
- Using Web3.py and Infura
![](/assets/server-side-ethereum-libraries-exercise-smart-contractsweb3-py-01.png)
![](/assets/server-side-ethereum-libraries-exercise-smart-contractsweb3-py-02.png)


# What is Light Wallet?
- Light wallet has 3 modules that provide functionality
  - **Keystore** - interface functions for the keystore object
  - **Signing** – interface function for signing raw transactions
  - **Txutils** - will create RLP encoded raw unsigned transactions 
- **Lightweight** **JS Wallet**for **Node** and the **browser**.
- **Allows you** to **store** your **encrypted keys** in the **browser**
- **Allows you**full control over your keys while still **connecting** to a **remote node** to **relay** signed transactions


# Installing Light Wallet
- Install using the node package manager
- Inside eth-lightwallet under  /node_modules folder is the lightwallet.min.js
- In case you don’t want to use it in the browser:
- Additionally, it exposes the lightwallet global object to the browser


# Using Light Wallet
- Generating a **wallet** (ignore the **require** line in the **browser**).


<!-- # Using Light Wallet -->
- Using the **Keystore object**we generated on the **previous slide**, we can **create and sign transactions**on **demand**. 


<!-- # Using Light Wallet -->
- Finally, we can **create** the **transaction** and **sign** it using our **derived key**
- After **signing** the transaction (**without substituting**the data **property**), you **should get**the following **output** (**signed** transaction) :


# Exercise: Light Wallet
- A minimal ethereum javascript wallet.
![](/assets/server-side-ethereum-libraries-exercise-light-wallet-01.png)
![](/assets/server-side-ethereum-libraries-exercise-light-wallet-02.png)


# Summary
- **Solc**– JavaScript bindings for the Solidity Compiler
- **Web3.js**– Ethereum JavaScript API
- **Ethers.js**– Complete Ethereum library in JavaScript
- **Nethereum**- .NET library for Ethereum
- **Web3j**– Java and Android Web3 alternative
- **Web3.py**– Python Web3 alternative
![](/assets/server-side-ethereum-libraries-summary-01.png)
