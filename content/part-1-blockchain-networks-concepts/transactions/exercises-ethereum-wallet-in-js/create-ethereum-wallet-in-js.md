# Exercises: Create Ethereum Wallet in JavaScript and Ethers.js

In this Exercise we are going to be learning how to create **Ethereum**
**wallet** with **JavaScript** and **ethers.js** libraries. During the
exercise you will install several **npm** packages, write the source
code for different functionalities and in the end, you will **send** and
**receive** ether coins with your wallet. 

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-01.png)

Download the Code Template from our Resources
---------------------------------------------

Extract the files from the provided Resources and you should have
something like this:

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-012.png)

Index.js holds all wallet endpoints and Todo comments that you need to
implement.

Install Packages
----------------

We need to install several packages for this exercise:

-   **express** -- Javascript web framework.

-   **ejs** -- Template engine.

-   **ethers** -- Library for interacting with the Ethereum blockchain.

You can install them with:

npm install

Start Implementing Todo's
-------------------------

We have 5 endpoints **create, load, send, balance** and **recover**
every endpoint has a **Todo** and you need to write there.

Example:

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-023.png)

1.  Add Constants

Here you only need to fill the missing information in the constant
**network** which we will use in the exercise. In this case it is
**ropsten** Testnet with **infura.io**. We will use another **constant**
for the working directory where we will store **encrypted** wallet
files.
![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-025.png)

2.  Implement **create** 1ich will generate and save wallet in our
    wallets directory.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-028.png)

### Test create wallet method

To start the project, write in cmd:

npm start

Output:

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-029.png)

Now our application is running on
[localhost:300](http://localhost:3000)0\
![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-030.png)Let's make a new wallet. Fill the form
with password and confirm your password.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-03.png)

If we go to our **wallet directory** we will find a file for your
wallet.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-04.png)

1.  Implement Load Wallet Endpoint

Here is the **load** endpoint which will read a file and **decrypt** it.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-06.png)

### Test load wallet method

Go to /**load** endpoint, fill your wallet filename and password and
submit the form.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-07.png)

2.  Implement Recover Wallet

With this method the users will generate new **json** file with their
**mnemonic** phrase

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-09.png)

### Test recover wallet

> Now let's assume that we want to use our wallet on the new computer.
> There isn't exist saved json file and we must recover our wallet from
> mnemonic phrase. Do you remember your mnemonic words? Did you hide
> them in the save place? Now take them, you will need to use these
> words. Go to /**recover** endpoint. Then write the **words** and type
> the **new password** and press \[**Submit**\]. Wallet will be
> successfully recovered.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-010.png)

3.  Implement Balance Endpoint

In this method we will derive 5 wallets and we will get their balance.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-013.png)

### Test balance method

1.  Let's see the balance of our
    wallet![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-015.png)

Request money from the faucet

Choose one of the addresses and copy it. Go to
<http://faucet.ropsten.be:3001/> , paste your address and wait 3-5
minutes. You can track your transaction status in etherscan.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-016.png)

If we check our balance now, we will find 1 ETH in the chosen account.
Copy the address and private key of the sender for the next step.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-017.png)

4.  Send Transaction Endpoint

Now we will **sign** and **broadcast** transaction to the ropsten
network.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-019.png)

### Test send transaction method

Let's transfer money between accounts. Copy another address from the
balance page as well as the private key of the address that has some
ETH.![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-020.png)

We will receive **Transaction hash** and we can track our transaction in
etherscan.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-022.png)

### Check Balance

Let's **check the balance** again. The second address was **received 1
ETH**. The total balance has lower than 1 ether because of the **fees**
payed for the transaction.

![](/assets/exercise-create-ethereum-wallet-with-js-and-ethers-024.png)

What to Submit?
===============

Create a **zip file** (e.g.
**your-name-create-ethereum-wallet-with-js-exercise.zip**) holding the
source code files and screen shots with your experiments.

Submit your zip file as **homework** at the course Web site.
