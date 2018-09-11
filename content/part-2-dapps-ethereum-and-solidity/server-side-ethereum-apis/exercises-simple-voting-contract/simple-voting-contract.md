# Exercises: Create a Simple Voting Contract and Invoke it through Web3.js

You will build a voting application where you will initialize a set of
candidates who will be contesting in the election and then vote for the
candidates. The votes will be stored on the blockchain. You will go
through the process of writing the voting contract, deploy to the
blockchain and interact with it.

Create the Smart Contract
-------------------------

1.  Create a new folder named **"Voting System"**. Open your command
    prompt and go in the folder.

2.  There, initialize truffle by the command:

  --------------
  truffle init
  --------------

3.  Create a new contract called **Voting.sol** and put it in
    **contracts** folder where will be our smart contract logic

4.  In the **migrations** folder create file **2\_deploy\_contracts.js**
    and add the following code which will deploy the smart contract

![](/assets/exercises-create-simple-voting-system-web3-01.png)

For the **Voting** contract:

5.  Create a **public** field, which for each candidate stores his
    votes.

6.  Create a **private** array storing every candidate.

7.  Create **addCandidate(string)** function, which adds the candidate
    to an array.

8.  Create **validCandidate(string)** function, which checks whether the
    given candidate is contained in the array.

9.  Then create function **voteForCandidate(string)**, which votes for
    given candidate.

10. Also, you will need to create function **totalVotesFor(string)**
    which will return the count of votes for a candidate.

11. To be able to compare strings we can first hash them with
    **keccak256()** and compare their hashes.

12. Maybe you should consider how to store the data as string or
    something else maybe ?

The contract source code is available here:

<https://pastebin.com/XfQPPmwa>

Setup the Development Environment
---------------------------------

1.  Install and start testrpc

  ------------------------------------
  npm install --g ethereumjs-testrpc
  ------------------------------------

![](/assets/exercises-create-simple-voting-system-web3-012.png)

2.  Install **node.js**

3.  Install **web3.js** library

  ---------------------
  npm install -g web3
  ---------------------

4.  In Windows environment you might run into error when trying to build
    this. If this happens, you should run the following code:

  -------------------------------------------------------------
  **npm install \--global \--production windows-build-tools**
  -------------------------------------------------------------

After that repeat the previous step and it should work fine.

5.  Run **node**

![](/assets/exercises-create-simple-voting-system-web3-018.png)

Compiling the Contract
----------------------

1.  Require the **web3** library:

![](/assets/exercises-create-simple-voting-system-web3-020.png)

2.  Now we want to get and store all our accounts that. We can do that
    with **web3.eth.getAccounts()**. This returns promise so what we are
    going to do is store the data in **accounts** Array that we will
    create to store the accounts.

![](3. Exercises-Create-Simple-Voting-System-Web3/media/image6.png)

3.  Now we want to read the contract and store it as variable so we can
    have an easy access for later use:

![](/assets/exercises-create-simple-voting-system-web3-023.png)

5.  Compile the code and you will get the bytecode, metadata, interface
    and so on:

![](/assets/exercises-create-simple-voting-system-web3-024.png)

Deploy the Contract
-------------------

1.  We should get the **abiDefinition** in JSON format by calling the
    command:

![](/assets/exercises-create-simple-voting-system-web3-02.png)

2.  Create **VotingContract**:

    Now we create the instance of the contract. Notice that we first
    give the ABI then in Object we give the account that we want to
    deploy from and the gas limit. In our case we have array with all of
    our accounts and we use the one at index 0.

![](/assets/exercises-create-simple-voting-system-web3-03.png)

3.  For the actual deployment we need the **byteCode** of the contract
    so we should get that now:

![](/assets/exercises-create-simple-voting-system-web3-04.png)

4.  Now we will **deploy** the contract and store the instance of the
    contract in **contractInstance**:

![](/assets/exercises-create-simple-voting-system-web3-05.png)

Interact with the Contract
--------------------------

1.  Now lets play with it and add few candidates and send them from
    different accounts (remember we have all accounts in our
    **accounts**\[\]):

![](/assets/exercises-create-simple-voting-system-web3-07.png)

We can see in both results the information about the transactions that
happened during the method executions and we can see that aswell in our
ganache.

![](/assets/exercises-create-simple-voting-system-web3-011.png)

Lets check our ganache again and see what happened there. We should have
some new transactions as writing in the contracts costs money.

![](/assets/exercises-create-simple-voting-system-web3-013.png)

3.  Check the votes for the candidates. Notice that we now don't use the
    **.send** as reading from contracts is free so we use **.call**
    instead.

    We still need to select what account we send from. That is because
    maybe we want to sent from owners account and have more access.

![](/assets/exercises-create-simple-voting-system-web3-017.png)

We can check again ganache to make sure that this reading didn't took
money from us.

![](/assets/exercises-create-simple-voting-system-web3-013.png)

And it seems that there is No new transactions so YES! It is free.

What to Submit?
===============

Submit as exercise outcome the **zip file with 3 images and the source
code.** The first image should be the one with the deployed contract
address, the second - adding of the candidates and the third one - the
votes of the candidates you added.
