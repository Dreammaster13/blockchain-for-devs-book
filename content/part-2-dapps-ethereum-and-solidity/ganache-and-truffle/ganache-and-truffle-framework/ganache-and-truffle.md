# Ganache and Truffle Framework

## Dev Tools for Ethereum and Solidity:Truffle Framework and Ganache

# Table of Contents
- Ganache
  - Accounts
  - Block Explorer
  - Ganache-cli
- Truffle Framework
  - Compile and Deploy Contracts
- Unit Testing
- Code coverage
![](/assets/truffle-and-ganache-table-of-contents-01.png)
![](/assets/truffle-and-ganache-table-of-contents-02.png)
![](/assets/truffle-and-ganache-table-of-contents-03.png)
![](/assets/truffle-and-ganache-table-of-contents-04.png)


# Ganache
- Run a Local Ethereum Development Network
![](/assets/truffle-and-ganache-ganache-01.png)


# What is Ganache?
- Ganache is part of the **Truffle Suite**
  - Quickly fire up a **personal Ethereum blockchain environment**
  - Ships with an internal **JavaScript-based** implementation of the **Ethereum blockchain**
  - Visual **mnemonic** & **account info**
  - See the current **status of all accounts**
![](/assets/truffle-and-ganache-what-is-ganache-01.png)


# Installing Ganache
![](/assets/truffle-and-ganache-installing-ganache-01.png)


# Ganache – Accounts
![](/assets/truffle-and-ganache-ganache-accounts-01.png)


# Ganache – Block Explorer
- Log output of Ganache’s **internal blockchain**
  - Responses and other vital **debugging information**
![](/assets/truffle-and-ganache-ganache-block-explorer-01.png)


<!-- # Ganache CLI (Command-Li -->
- Command-line Ethereum environment (formerly called TestRPC)
- Run **ganache-cli** as docker image
- Install **ganache-cli**as local Node.js package
- Run **ganache-cli**from the console:


<!-- # Ganache CLI (Command-Li -->
![](/assets/truffle-and-ganache-ganache-cli-command-line-01.png)


# Connecting from Remix IDE to Ganache
![](/assets/truffle-and-ganache-connecting-from-remix-ide-to-ganache-01.png)
![](/assets/truffle-and-ganache-connecting-from-remix-ide-to-ganache-02.png)
![](/assets/truffle-and-ganache-connecting-from-remix-ide-to-ganache-03.png)


# Truffle Framework
- Development Environment, Testing Framework and Asset Pipeline for Ethereum
![](/assets/truffle-and-ganache-truffle-framework-01.png)


# Truffle
- Truffle provides tools for smart contract development
  - Compilation of contracts
  - Deployment of contracts
  - Interactive console
  - Local EVM environment
  - **Unit testing**for smart contracts
- Scriptable, extensible deployment & migrations framework
![](/assets/truffle-and-ganache-truffle-01.png)


# Truffle
- Network management for **deploying** to public & private networks
- Package management with **EthPM** & **NPM**
  - Using the **ERC190** standard
- Interactive **console** for direct contract communication
- Configurable build pipeline with support for tight integration
- External script runner that executes **scripts** within a **Truffle environment**
- Installing Truffle

```cs
npm install -g truffle
```



# Running Truffle
- Just type "**truffle**" at the console
- In Windows use **PowerShell**, not the "Command Prompt"
  - Or you will get a JScript error 
![](/assets/truffle-and-ganache-running-truffle-01.png)
![](/assets/truffle-and-ganache-running-truffle-02.png)


# Truffle: Creating a New Empty App

```cs
mkdir truffle-example
cd truffle-example
```

![](/assets/truffle-and-ganache-truffle-creating-a-new-empty-app-01.png)


<!-- # Truffle: Adding Contracts (Solidity Co -->
- Put your Solidity code in your project's **contracts/** directory

```cs
contracts/SimpleStorage.sol
```



# Truffle: Compiling Contracts
- Compile your Truffle project
- The output is in **build/contracts/{filename}.json**

```cs
truffle compile
```

![](/assets/truffle-and-ganache-truffle-compiling-contracts-01.png)
![](/assets/truffle-and-ganache-truffle-compiling-contracts-02.png)
![](/assets/truffle-and-ganache-truffle-compiling-contracts-03.png)


# Truffle: Run Ganache or Ganache CLI
![](/assets/truffle-and-ganache-truffle-run-ganache-or-ganache-cli-01.png)


# Truffle: Configure Networks
<div class="fragment balloon" style="top:25.77%; left:70.09%; width:45.67%">Define your **Ethereum networks** and their RPC</div>
<div class="fragment balloon" style="top:59.40%; left:51.99%; width:42.31%">Connect to your **local Ganache** RPC server</div>


# Truffle Dev Console

```cs
truffle console
```

![](/assets/truffle-and-ganache-truffle-dev-console-01.png)


# Truffle Deployment: Migrate
- First, add a new migration to deploy your new contracts:
- Execute the migrations to get your contracts deployed:

```cs
truffle migrate
```



# Truffle Deployment: Execute the Migrations
![](/assets/truffle-and-ganache-truffle-deployment-execute-the-migrations-01.png)


# Interacting with the Deployed Contracts
- Get an **instance** of the deployed contract
- Inspect the contract instance:
![](/assets/truffle-and-ganache-interacting-with-the-deployed-contracts-01.png)


# Invoking Contract's Functionality
![](/assets/truffle-and-ganache-invoking-contract-s-functionality-01.png)
![](/assets/truffle-and-ganache-invoking-contract-s-functionality-02.png)


# Creating a New Contract Instance
- Create a new **instance** of existing contract
- Inspect the contract instance:


# Truffle: Unit Testing Smart Contracts

```cs
test/TestSimpleStorage.js
```



# Testing a Smart Contract
<div class="fragment balloon" style="top:30.25%; left:80.86%; width:44.08%">Create **new** instance of **token** before each test  </div>
<div class="fragment balloon" style="top:64.05%; left:84.61%; width:34.59%">Check if the initial **totalSupply** is 0</div>


# Truffle: Running the Tests
![](/assets/truffle-and-ganache-truffle-running-the-tests-01.png)


# Time-Travel

```cs
timeTravel: (web3, seconds) => {
    return new Promise((resolve, reject) => {
        web3.currentProvider.sendAsync({jsonrpc: "2.0",
            method: "evm_increaseTime", params: [seconds],
            id: new Date().getTime()
        }, (err, result) => {
            if(err) return reject(err);    
            web3.currentProvider.sendAsync({jsonrpc: "2.0",
                method: "evm_mine", id: new Date().getTime()
            }, (err,result) => {
                   return err ? reject(err) : resolve(result);                    
            });
        });
    });
}
```



# Time-Travel Unit Test
![](/assets/truffle-and-ganache-time-travel-unit-test-01.png)


# Other Useful Utility Methods
- Watch an event:

```cs
watchEvent: (event) => {
    return new Promise((resolve, reject) => {
        event.watch((err, res) => {
            if (err) reject(err);
            resolve(res);
        }
    }
}
```



# Solidity Coverage
- **Code coverage** for Solidity testing
  - Generates an **HTML report**
    - Uses **Istanbul** Code Coverage (https://istanbul.js.org/)
  - Expects a **globally installed Truffle**
  - Uses **instrumentation** like most coverage tools (high gas usage)
![](/assets/truffle-and-ganache-solidity-coverage-01.png)


<!-- # Solidity Coverage -->
- Generates a stub **truffle.js**(**truffle-config.js**) that accommodates its special gas
- Connects to a coverage-enabled 
-    fork of **ganache-cli** called
-    **testrpc-sc** on port **8555**
-  

```cs
./node_modules/.bin/solidity-coverage
```

![](/assets/truffle-and-ganache-solidity-coverage-2-01.png)


# Front-End Frameworks in Truffle
- **Angular**
- **React**
- **Vue.js**
![](/assets/truffle-and-ganache-front-end-frameworks-in-truffle-01.png)
![](/assets/truffle-and-ganache-front-end-frameworks-in-truffle-02.png)
![](/assets/truffle-and-ganache-front-end-frameworks-in-truffle-03.png)


# Truffle Boxes
- Helpful **boilerplates**
  - Everything needed to start a smart-contract based web app
- react – http://truffleframework.com/boxes/react 
- react-auth – http://truffleframework.com/boxes/react-auth
- react-uport – http://truffleframework.com/boxes/react-uport 
- tutorialtoken – http://truffleframework.com/boxes/tutorialtoken 
- webpack – http://truffleframework.com/boxes/webpack 


# Exercise: Install Truffle and Ganache
- Development Environment and Framework
![](/assets/truffle-and-ganache-exercise-install-truffle-and-ganache-01.png)


# Summary
- **Ganache**
  - Testing Ethereum environment for developers
  - Available as GUI and command-line
- **Truffle Framework**
  - Framework and tools for Solidity development
  - Starter kits (boxes)
  - Compile, migrate, deploy, run
- **Unit Testing**
  - Code coverage
![](/assets/truffle-and-ganache-summary-01.png)

# Resources
- Truffle Framework:
  - http://truffleframework.com
  - http://truffleframework.com/docs/ 
- Ganache:
  - http://truffleframework.com/ganache/
  - http://truffleframework.com/docs/ganache/using




