# Exercises: Building an Simple Ethereum Wallet in JavaScript

In this exercise, you shall implement a **simple Ethereum wallet** in
JavaScript, using the [Ethers.js
library](https://github.com/ethers-io/ethers.js). The wallet will hold a
**single private key** along with its associated Ethereum address.

Introduction
------------

The [**Wallet**
class](https://github.com/ethers-io/ethers.js/blob/master/wallet/wallet.js)
in the Ethers.js library holds: **private key** + **address** + ability
to **sign** transactions. Let's play with it.

**Create** a new JavaScript project. To get **ethers.js** either install
it through the NPM package manager:

  ----------------------------
  npm install \--save ethers
  ----------------------------

Or just download the ready-to-use JS library code:

-   <https://cdn.ethers.io/scripts/ethers-v2.min.js>

New Wallet by Private Key
-------------------------

First, create a function, which by a given private key returns a
**Wallet** instance. The wallet instance has the wallet\'s private key,
address, and functionality to sign.

This is the Private Key that you can use:

  ------------------------------------------------------------------------
  **0x495d5c34c912291807c25d5e8300d20b749f6be44a178d5c50f167d495f3315a**
  ------------------------------------------------------------------------

![](/assets/exercise-simple-ethereum-wallet-in-js-04.png)

New Random Wallet
-----------------

Second, create a method that returns a random generated **Wallet** using
**ethers.Wallet.createRandom**. This method create for you a random
mnemonic by entropy then from the hierarchical node derives once and
creates a wallet from its private key. As you can see, the instance
stores the mnemonic and the derivation path.

![](/assets/exercise-simple-ethereum-wallet-in-js-06.png)

Save Wallet as JSON
-------------------

Create a method called **saveWalletToJSON**, which takes a **Wallet**
instance and a password and returns a JSON V3 Keystore. Use the wallet's
**encrypt** method.

Private Key:
**0x495d5c34c912291807c25d5e8300d20b749f6be44a178d5c50f167d495f3315a**

Password: **p@\$\$w0rd\~3**

![](/assets/exercise-simple-ethereum-wallet-in-js-08.png)

Load Wallet from JSON
---------------------

Create a method that takes a json and a password, decrypts the json and
returns a wallet instance. Use **ethers.Wallet.fromEncryptedWallet(json,
password).**

Private Key:
**0x495d5c34c912291807c25d5e8300d20b749f6be44a178d5c50f167d495f3315a**

Password: **p@\$\$w0rd\~3**

![](/assets/exercise-simple-ethereum-wallet-in-js-010.png)

Sign a Transaction
------------------

Create a method that signs a transaction and returns it. To build a
transaction you need:

![](/assets/exercise-simple-ethereum-wallet-in-js-011.png)

Private Key:
**0x495d5c34c912291807c25d5e8300d20b749f6be44a178d5c50f167d495f3315a**

toAddress: **0x7725f560672A512e0d6aDFE7a761F0DbD8336aA7**

![](/assets/exercise-simple-ethereum-wallet-in-js-03.png)

What to Submit?
===============

Create a **ZIP file** (e.g.
**your-name-simple-ethereum-wallet-exercise.zip**) holding your source
code for all problems. Submit your ZIP file as **homework** at the
course Web site.
