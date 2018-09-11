# Exercises: Using Web3.py to Access Ethereum Smart Contracts from Python

In this exercise, we will use **web3.py** library for interacting with
Ethereum. Its API is derived from the Web3.js JavaScript API and should
be familiar to anyone who has used web3.js. The exercise will show how
to **interact** with an already **deployed** contract on the
**Ethereum** **Ropsten** **Testnet**.

Set up environment
------------------

Web3.py requires Python 3. It can be installed using **pip** as follows.

  ------------------
  pip install web3
  ------------------

**Create** a new Python file and import the following:

![](/assets/exercises-smart-contracts-web3.py-01.png)

We will need **HTTPProvider** in order to create our connection to the
Ropsten Testnet using **Infura.io.**

Now let's get the necessary Infura.io provider. **Go** to
<https://infura.io/> and click **\[Get started for free\]**:

![](/assets/exercises-smart-contracts-web3.py-011.png)

Fill out the form and click **\[Submit\]**. Then **copy** the Ropsten
URL:

![](/assets/exercises-smart-contracts-web3.py-013.png)

In order to get a contract instance of an already deployed contract, we
will need its address and application binary interface. For exercise's
purpose, **deploy** a simple contract storing an array of facts through
**Remix IDE** using **MetaMask Ropsten** a provider:

![](/assets/exercises-smart-contracts-web3.py-014.png)

If you do not have ETHt, use the **MetaMask** faucet:
<https://faucet.metamask.io/>

Then, **copy** its **address** and **ABI,** and create an instance of
the contract. **Json** library will be needed to the decode the ABI:

![](/assets/exercises-smart-contracts-web3.py-015.png)

Writing to the Smart Contract
-----------------------------

Now that there is an instance of the contract, create a method for
writing facts in the smart contract. It will need the **instance**, a
**private key/wallet**, the **address** of the private key/wallet and
the fact. The library **is not recommended to work** with Local Private
Keys in Production **at the moment**, so for the exercise we will enable
the unaudited features.

![](/assets/exercises-smart-contracts-web3.py-016.png)

Because the **contract owner** can only add facts to this contract,
**copy** his **private** **key** and his **address**.

![](/assets/exercises-smart-contracts-web3.py-018.png)

Copy the **private key** and the **address**. The address will be needed
to easily **calculate** the **nonce**:

![](/assets/exercises-smart-contracts-web3.py-03.png)

We will **create** a simple transaction, which **adds** a fact to the
contract, **sign** it with the private key and send it.

![](/assets/exercises-smart-contracts-web3.py-06.png)

Try **adding** a fact using **another** **private key.**

Reading from the Smart Contract
-------------------------------

When reading from a Smart Contract, no wallets or private keys are
needed.

First, **create** a method which gets a fact by a given index:

![](/assets/exercises-smart-contracts-web3.py-08.png)

Then **create** a method, which gets how many facts are stored in the
contract:

![](/assets/exercises-smart-contracts-web3.py-010.png)

What to Submit?
===============

Create a **zip file** (e.g.
**username-playing-smart-contracts-web3-py.zip**) holding the Python
file with the methods, a snapshot of the Ropsten Etherscan contract
address and its transactions.

Submit your **zip** file as **homework** at the course Website.
