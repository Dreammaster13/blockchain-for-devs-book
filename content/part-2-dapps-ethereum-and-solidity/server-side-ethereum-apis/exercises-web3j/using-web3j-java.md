# Exercises: Using Web3j to Access Ethereum Smart Contracts from Java

In this exercise, we will use **Web3j** -- Lightweight Java and Android
library for integration with Ethereum clients.

This exercise will show how to create contract wrappers from native java
code, deploy contracts and how to **interact** with an already
**deployed** contract on the **Ethereum** **Ropsten** **Testnet**.

Set up environment
------------------

First, **create** a new **Maven** **Project**:

![](/assets/exercises-smart-contracts-web3j-012.png)

In order to create a wrapper class of the contract we will need to
compile it and create two files with bytecode and the application binary
interface.

Install solc:

  ----------------------
  npm install --g solc
  ----------------------

Create a **.sol** called **ArrayOfFacts**, which will have 3 functions:
**adding** a fact, **get** a fact by an **index** and **get** how many
**facts** are stored in the contract:

![](/assets/exercises-smart-contracts-web3j-023.png)

To **generate** the wrapper code, compile the smart contract and create
the bytecode and abi in the same directory:

  --------------------------------------------------------
  solcjs ArrayOfFacts.sol \--bin \--abi \--optimize -o .
  --------------------------------------------------------

![](/assets/exercises-smart-contracts-web3j-025.png)

Finally, to generate the wrapper code, use **web3j's Command Line
Tools**. Go to <https://github.com/web3j/web3j/releases> and
**download** the **release** appropriate for your OS. Extract it,
**open** a terminal in the **bin** **directory** and **run:**

  ---------------------------------------------------------------------------------------------------------------------------------------------------
  web3j solidity generate /path/to/\<smart-contract\>.bin /path/to/\<smart-contract\>.abi --o /path/to/src/main/java --p com.your.organisation.name
  ---------------------------------------------------------------------------------------------------------------------------------------------------

This will **create** a wrapper class of the contract:

![](/assets/exercises-smart-contracts-web3j-026.png)

Then, create a class called **ContractService**, which will handle the
connection Ropsten and handle the contract\'s deployment, load and call
of it**. Create** 3 private properties for the **Web3**, the
**Credentials** (account) and for the **Contract** itself.

![](/assets/exercises-smart-contracts-web3j-027.png)

Then, **create** a constructor, which takes **2** parameters:
**provider** of the node and a **private key** for the credentials:

![](/assets/exercises-smart-contracts-web3j-028.png)

We will need **HTTPProvider** in order to create our connection to the
Ropsten Testnet using **Infura.io.**

Now let's get the necessary Infura.io provider. **Go** to
<https://infura.io/> and click **\[Get started for free\]**:

![](/assets/exercises-smart-contracts-web3j-029.png)

Fill out the form and click **\[Submit\]**. Then **copy** the Ropsten
URL:

![](/assets/exercises-smart-contracts-web3j-030.png)

**Create** a Main.java file and paste in the **main**:

![](/assets/exercises-smart-contracts-web3j-02.png)

For the example of the exercise, we will take one private key from
**MetaMask** and use it as a signer for the deployment transaction. Keep
in mind **only** the **contract** owner can add facts to the contract.

![](/assets/exercises-smart-contracts-web3j-03.png)

If you do not have ETHt, use the **MetaMask** faucet:
<https://faucet.metamask.io/>

![](/assets/exercises-smart-contracts-web3j-07.png)

Go to **ContractService.java** and create a deploy method, which creates
a transaction for the deployment of the contract and then **sends** it.
The method will **wait** to for the transaction to be **mined** and then
finish**:**

![](/assets/exercises-smart-contracts-web3j-010.png)

Copy the contract address and create a load function, which loads a
contract by its address:

![](/assets/exercises-smart-contracts-web3j-013.png)

Writing to the Smart Contract
-----------------------------

In the **ContractService** class, create a method, which takes as an
argument a fact, calls the contract\'s add function and sends it. The
result will return when the transaction is mined:

![](/assets/exercises-smart-contracts-web3j-017.png)

Try **adding** a fact using **another** **private key as an account.**

Reading from the Smart Contract
-------------------------------

When reading from a Smart Contract, no wallets or private keys are
needed.

In the **ContractService** class **create** a method which gets a fact
by a given index and returns a string with the fact.

![](/assets/exercises-smart-contracts-web3j-020.png)

Then **create** a method, which gets how many facts are stored in the
contract:

![](/assets/exercises-smart-contracts-web3j-024.png)

What to Submit?
===============

Create a **zip file** (e.g.
**username-playing-smart-contracts-web3j.zip**) holding the 3 **java**
files (**Contract**, **ContractService** and **Main**) with the methods,
a snapshot of the Ropsten Etherscan contract address and its
transactions.

Submit your **zip** file as **homework** at the course Website.
