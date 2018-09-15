# Exercises: Deploy a Solidity Smart Contract in Quorum

The goal of this exercise is to install and setup **Quorum**. Quorum is
a **permissioned blockchain software.** Follow the instruction below and
you will make a private blockchain platform suitable for enterprise
cases.

For this exercise we will use windows, but we will need some additional
software for virtualization to keep things clear. The software that we
need are **VirtualBox** and **Vagrant.**

Install VirtualBox
------------------

1.  We will use VirtualBox to make instance of our blockchain. You can
    download VirtualBox from here
    <https://www.virtualbox.org/wiki/Downloads>, choose the version for
    your OS.

2.  Run the installer wizard and press next.

    ![](/assets/exercises-install-quorum-and-deploy-smart-contract-06.png)

Install Vagrant
---------------

1.  Go to <https://www.vagrantup.com/downloads.html> and download
    vagrant for your OS.

2.  Run the installer and press **\[next\]**

    ![](/assets/exercises-install-quorum-and-deploy-smart-contract-08.png)

After successful install restart your computer.

Install Quorum and Run Your Own Blockchain
------------------------------------------

1.  Now when we have VirtualBox and Vagrant we can run **Quorum.** First
    we need to clone the examples repository.

  ------------------------------------------------------------
  git clone https://github.com/jpmorganchase/quorum-examples
  ------------------------------------------------------------

2.  Navigate to the **quorum-examples** directory

  ------------------------
  **cd quorum-examples**
  ------------------------

3.  Now start a Vagrant instance in the folder

  ----------------
  **vagrant up**
  ----------------

4.  Now **Vagrant** will make a ubuntu instance in your virtual machine
    and download all that is necessary for **Quorum.** This will take a
    while, give 5 minutes break for yourself. When you are ready you
    will receive this output

![](/assets/exercises-install-quorum-and-deploy-smart-contract-09.png)

5.  Now we have a virtual machine with everything needed to build Quorum
    network and you can access it with

  -----------------
  **vagrant ssh**
  -----------------

![](/assets/exercises-install-quorum-and-deploy-smart-contract-010.png)

6.  Now go to **7nodes** example. When we run it, you will make network
    with 7 nodes.

  -----------------------
  **cd quorum-example**
  -----------------------

7.  Now we need to add the consensus mechanism we will use **raft** for
    this tutorial. Type in the terminal the file that will configure our
    raft consensus.

  --------------------
  **./raft-init.sh**
  --------------------

The output will be like this one

![](/assets/exercises-install-quorum-and-deploy-smart-contract-011.png)

8.  After successful initialization we need to start **raft** consensus,
    you can do that with this file

![](/assets/exercises-install-quorum-and-deploy-smart-contract-012.png)

Now we have 7 nodes that are running in our network.

9.  Now we can deploy pre-defined contract with this script

  ----------------------------------------
  **./runscript.sh private-contract.js**
  ----------------------------------------

The output will be the transaction hash from the transaction.

![](/assets/exercises-install-quorum-and-deploy-smart-contract-02.png)

Now run the first node with

  ------------------------------------
  **geth attach qdata/dd1/geth.ipc**
  ------------------------------------

JavaScript terminal will start

![](/assets/exercises-install-quorum-and-deploy-smart-contract-03.png)

10. Now we can check the transaction hash and take the contract address.

  ---------------------------------------------------------------
  **web3.eth.getTransactionReceipt('YOUR\_TRANSACTION\_HASH')**
  ---------------------------------------------------------------

![](/assets/exercises-install-quorum-and-deploy-smart-contract-04.png)

Make a private transaction for contract
---------------------------------------

Now we need to open 3 terminals for the different accounts that we have.

1.  Open 3 terminals navigate to the Quorum repository and run vagrant
    there.

In terminal 1 run:

  ----------------------------------------
  **geth attach ipc:qdata/dd1/geth.ipc**
  ----------------------------------------

In terminal 2 run:

  ----------------------------------------
  **geth attach ipc:qdata/dd4/geth.ipc**
  ----------------------------------------

In terminal 3 run:

  ----------------------------------------
  **geth attach ipc:qdata/dd7/geth.ipc**
  ----------------------------------------

2.  After that in each terminal define the contract

+-----------------------------------------------------------------------+
| **var contractAddress = 'YOUR\_CONTRACT\_ADDRESS'**                   |
|                                                                       |
| **var abi =                                                           |
| \[{\"constant\":true,\"inputs\":\[\],\"name\":\"storedData\",\"output |
| s\":\[{\"name\":\"\",\"type\":\"uint256\"}\],\"payable\":false,\"type |
| \":\"function\"},{\"constant\":false,\"inputs\":\[{\"name\":\"x\",\"t |
| ype\":\"uint256\"}\],\"name\":\"set\",\"outputs\":\[\],\"payable\":fa |
| lse,\"type\":\"function\"},{\"constant\":true,\"inputs\":\[\],\"name\ |
| ":\"get\",\"outputs\":\[{\"name\":\"retVal\",\"type\":\"uint256\"}\], |
| \"payable\":false,\"type\":\"function\"},{\"inputs\":\[{\"name\":\"in |
| itVal\",\"type\":\"uint256\"}\],\"type\":\"constructor\"}\];**        |
|                                                                       |
| **var contract = eth.contract(abi).at(contractAddress)**              |
+-----------------------------------------------------------------------+

3.  Now go to first terminal and call **get**() method of the contract.

  ----------------
  contract.get()
  ----------------

Output will be 42.

4.  Now we will use **privateFor** option to make private transaction
    that only **first** and **third** terminal can see.
    **ROAZBWtSacxXQrOe3FGAqJDyJjFePR5ce4TSIzmJ0Bc=** is derived from the
    third account public key.

  ----------------------------------------------------------------------------------------------------------
  **contract.set(4,{from:eth.coinbase,privateFor:\[\"ROAZBWtSacxXQrOe3FGAqJDyJjFePR5ce4TSIzmJ0Bc=\"\]});**
  ----------------------------------------------------------------------------------------------------------

Now if you go to the first terminal the output will be

  ----------------
  **Output : 4**
  ----------------

If you open the second terminal, the output will be zero, because the
data is hidden for him:

  ----------------
  **Output : 0**
  ----------------

If you open the third terminal where we allow access to the transaction,
you will se the number that we expect.

  ----------------
  **Output : 4**
  ----------------

What to Submit?
===============

Create a **zip file** (e.g.
**your-name-qorum-smart-contracts-exercise.zip**) holding the
screenshots with your experiments. Make screenshots of console with
running node, migrations and contract's transactions.

Submit your **zip** file as **homework** at the course Web site.
