# Exercises: Using Nethereum to Access Ethereum Smart Contracts from C#

In this exercise, we will use **Nethereum .NET integration** library for
Ethereum, simplifying the access and smart contract interaction with
Ethereum nodes. The exercise will show how to **interact** with an
already **deployed** contract on the **Ethereum** **Ropsten**
**Testnet**.

Setup the Development Environment
---------------------------------

**Create** a .NET Core Console Application and **install** the following
**NuGetPackages**:

![](/assets/exercises-smart-contracts-nethereum-web3-01.png)

Create a class called **ContractService**, which will be the connection
to the **Ropsten Testnet. Create** 3 readonly private properties for the
**Web3**, the **Contract** and for an **Account**, which will be the
wallet.

![](/assets/exercises-smart-contracts-nethereum-web3-012.png)

Then, create a constructor, which takes 4 parameters: provider of the
node, contract address, contract abi and a private key for an
account/wallet.

![](/assets/exercises-smart-contracts-nethereum-web3-016.png)

We will need **HTTPProvider** in order to create our connection to the
Ropsten Testnet using **Infura.io.**

Now let's get the necessary Infura.io provider. **Go** to
<https://infura.io/> and click **\[Get started for free\]**:

![](/assets/exercises-smart-contracts-nethereum-web3-017.png)

Fill out the form and click **\[Submit\]**. Then **copy** the Ropsten
URL:

![](/assets/exercises-smart-contracts-nethereum-web3-019.png)

In order to get a contract instance of an already deployed contract, we
will need its address and application binary interface. For exercise's
purpose, **deploy** a simple contract storing an array of facts through
**Remix IDE** using **MetaMask Ropsten** a provider:

![](/assets/exercises-smart-contracts-nethereum-web3-020.png)

If you do not have ETHt, use the **MetaMask** faucet:
<https://faucet.metamask.io/>

Then, **copy** its **address** and **ABI,** and create an instance of
the contract.
![](/assets/exercises-smart-contracts-nethereum-web3-021.png)

Because the **contract owner** can only add facts to this contract,
**copy** his **private** **key**.

![](/assets/exercises-smart-contracts-nethereum-web3-02.png)

Copy the **private key** and the **address**. The address will be needed
to easily **calculate** the **nonce**:

![](/assets/exercises-smart-contracts-nethereum-web3-04.png)

Writing to the Smart Contract
-----------------------------

In the **ContractService** class, create a method, which takes as an
argument a fact and adds it to the contract. We will send an
asynchronous transaction - **method.SendTransactionAsync(from, gas,
value, functionInput)** and will not wait to be mined, just get the
transaction hash.

![](/assets/exercises-smart-contracts-nethereum-web3-08.png)

Try **adding** a fact using **another** **private key as an account.**

Reading from the Smart Contract
-------------------------------

When reading from a Smart Contract, no wallets or private keys are
needed.

In the **ContractService** class **create** a method which gets a fact
by a given index and returns a string with the fact. Get the method of
the contract and then make an asynchronous call with the index as
parameter, which will return **Task\<string\>** and get the result:

![](/assets/exercises-smart-contracts-nethereum-web3-011.png)

Then **create** a method, which gets how many facts are stored in the
contract:

![](/assets/exercises-smart-contracts-nethereum-web3-015.png)

What to Submit?
===============

Create a **zip file** (e.g.
**username-playing-smart-contracts-nethereum-web3.zip**) holding the two
**.cs** files with the methods, a snapshot of the Ropsten Etherscan
contract address and its transactions.

Submit your **zip** file as **homework** at the course Website.
