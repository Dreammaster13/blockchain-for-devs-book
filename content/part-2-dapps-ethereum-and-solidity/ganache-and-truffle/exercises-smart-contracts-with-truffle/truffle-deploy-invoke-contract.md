# Exercises: Develop, Deploy and Invoke Smart Contracts with Truffle

The goal of this exercise is to **create smart contract**, compile and
deploy it using the **Truffle Framework** and add **unit tests** for the
contract logic using **Truffle**. We will deploy the smart contract in
Ganache-CLI with Truffle. Then write unit tests for the smart contract
and test it with Truffle. The contract will be written in **Solidity**.
Before we get started, you must have Truffle and **Ganache-cli**
installed. Ganache-cli will be the tool we will use to create a
**private blockchain** that runs on our machine only.

For this exercise we will use Ubuntu 16.04.3.

Set the Truffle and Ganache-cli
-------------------------------

1.  If you already have **Ganache-cli** installed just skip this step,
    otherwise open terminal console and write command:

  ------------------------------------
  \$ sudo npm install -g ganache-cli
  ------------------------------------

**In Windows**:

  -------------------------------
  \$ npm install -g ganache-cli
  -------------------------------

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-01.png)

2.  Create folder **Exercise** and open console. Create **truffle
    project** here by writing command: "**truffle init**". Truffle will
    install three folders.

    -   In folder **contracts**: we will save our smart contracts.

    -   In **migrations**: we will hold configuration files for
        migrations. They are .js files starts with number, like
        1\_initial\_migration.js and 2\_deploy\_contracts.js.

    -   Folder **test**: holds unit test files.

> The file truffle.js is truffle configuration file.

  -----------------
  \$ truffle init
  -----------------

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-03.png)

3.  **In Linux**: Open **truffle.js** file and make it looks like the
    picture. The port in which ganache-cli communicates is **8545**.

    ![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-04.png)

4.  **In Windows**: In the root folder, you'll see two files,
    "**truffle.js**" and "**truffle-config.js**". **Remove
    "truffle.js"**. The reason for that is, on Windows there is a naming
    problem, and when we will want to execute Truffle commands, it will
    open the config file "truffle.js" instead of reading what's inside.
    Then put this code inside of "**truffle-config.js**":

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-05.png)

Deploy a Smart Contract
-----------------------

1.  Now is time to **write our smart contract**. Open **Remix** Solidity
    IDE. The contract allows you to publish a time-limited article with
    name and text. Modifier **onlyOwner** allows only the owner of the
    contract to modify the articleName and articleText. Modifier
    **limitedTime** restricts for how long the article is readable.
    Write the following solidity code in Remix. Click **Start to
    compile** to compile and verify the contract.

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-06.png)

2.  Now, copy the code of the smart contract. Open the **contracts**
    directory, create file **PublicArticle.sol** in there and pastе the
    copied code in the file.

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-07.png)

3.  Go to **migrations** folder and create file
    **2\_deploy\_contracts.js** with the following content:

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-08.png)

4.  Now, you are ready to compile the contract and migrate it to
    ganache-cli blockchain. Open console and run ganache-cli. The local
    testnet will started and gives you 10 addresses and 10 private keys.
    If you don\`t declare something else the first "0" address will be
    used by default. If you deploy contract with him, it will be the
    owner\`s address.

  ----------------
  \$ ganache-cli
  ----------------

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-09.png)

5.  Open second terminal, go to Exercise directory and type:

  --------------------
  \$ truffle migrate
  --------------------

**NOTE:** On Windows you should write **truffle.cmd migrate** instead,
because there is a JS file with the same name in the main folder and
cmd.exe will get confused.

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-010.png)

The smart contract was **successfully deployed**. You can see the
**transaction number** wrote in **block 4** of the blockchain.

6.  Now run the **truffle console** and call the info for **block 4.**
    There is the transaction number which we see in migration info.

  --------------------
  \$ truffle console
  --------------------

  -------------------------
  \> web3.eth.getBlock(4)
  -------------------------

![](/assets/exercise-develop-and-deploy-smart-contracts-with-truffle-02.png)

What to Submit?
===============

Create a **zip file** (e.g.
**your-username**-**contracts-truffle-unit-tests-exercise.zip**) holding
the screenshots with your experiments.

Submit your **zip** file as **homework** at the course Web site.
