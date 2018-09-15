# Exercises: Deploy a Solidity Smart Contract in the Qtum Testnet

In this exercise, you will deploy a simple Smart Contract in Qtum
Regtest. To deploy a contract you will need the contract\'s **bytecode**
and **abi**, **generated** with **solcjs**. Then you will deploy the
Contract. Finally yet importantly, invoke its methods in JavaScript
using **qweb3.js**.

Generate Bytecode and ABI
-------------------------

![](/assets/exercises-deploy-smart-contract-qtum-01.png)

  ----------------------
  npm install --g solc
  ----------------------

Compile the contract

  ----------------------------------------
  solcjs SimpleStorage.sol \--bin \--abi
  ----------------------------------------

You will need the bytecode later to deploy the contract and the ABI to
interact with it.

Run Qtum regtest
----------------

1.  Download the latest release of Qtum -
    <https://github.com/qtumproject/qtum/releases>

![](/assets/exercises-deploy-smart-contract-qtum-09.png)

2.  Extract it, go to **bin** folder and run the daemon on **regtest**
    network with username, password and port. If you want, you can set
    your data directory to be at an appropriate for you place

  ----------------------------------------------------------------------------
  qtumd.exe \--regtest \--datadir=. -rpcuser=a -rpcpassword=b -rpcport=13889
  ----------------------------------------------------------------------------

![](/assets/exercises-deploy-smart-contract-qtum-010.png)

3.  Qtum **regtest** provides the option to generate blocks in order to
    speed up the process using **PoW**. To get some **QTUM, Open a new
    Terminal** and **generate** 500 blocks using **qtum-cli**

  -------------------------------------------------------------------------------
  qtum-cli.exe \--regtest -rpcuser=a -rpcpassword=b -rpcport=13889 generate 500
  -------------------------------------------------------------------------------

![](/assets/exercises-deploy-smart-contract-qtum-011.png)

4.  To check the wallet\'s address and current balance, type
    **getwalletinfo**

  --------------------------------------------------------------------------------
  qtum-cli.exe \--regtest -rpcuser=a -rpcpassword=b -rpcport=13889 getwalletinfo
  --------------------------------------------------------------------------------

![](/assets/exercises-deploy-smart-contract-qtum-012.png)

Deploy Contract
---------------

1.  To deploy the contract, call **createcontract** with the bytecode

  --------------------------------------------------------------------------------------------------------
  qtum-cli.exe \--regtest -rpcuser=a -rpcpassword=b -rpcport=13889 createcontract 6060604052341561000...
  --------------------------------------------------------------------------------------------------------

![](/assets/exercises-deploy-smart-contract-qtum-013.png)

2.  The result is a JSON, storing the **transaction hash**, **sender
    address**, **hash160** and the **address** of the contract

![](/assets/exercises-deploy-smart-contract-qtum-014.png)

Save the **sender address** and the **contract address!**

3.  Mine one block using **generate**

![](/assets/exercises-deploy-smart-contract-qtum-015.png)

4.  Check whether the transaction is **confirmed** using
    **gettransaction**:

![](/assets/exercises-deploy-smart-contract-qtum-016.png)

5.  Check what is behind the address of the contract using
    **getaccountinfo**

![](/assets/exercises-deploy-smart-contract-qtum-02.png)

Setup qweb3.js
--------------

1.  Create a new **JavaScript** project and import **qweb3.js**

  npm init -y
  -------------------------------
  npm install \--save-dev qweb3

2.  **Import** the necessary dependencies

![](/assets/exercises-deploy-smart-contract-qtum-03.png)

3.  **Create** the contract instance using the **contract address**,
    **abi** and **rpc**. Copy the ABI from the **solc** generation

![](/assets/exercises-deploy-smart-contract-qtum-04.png)

4.  **Set** the value of the variable in the contract. Use as a sender
    address the creator of the contract

> ![](/assets/exercises-deploy-smart-contract-qtum-06.png)
>
> **Mine the transaction!**

6.  **Get** the value of the contract

> ![](/assets/exercises-deploy-smart-contract-qtum-08.png)

What to Submit?
===============

Create a **zip file** (e.g. **username-deploy-smart-contract-qtum.zip**)
holding the JavaScript file with the contract invocation.

Submit your **zip** file as **homework** at the course Website.
