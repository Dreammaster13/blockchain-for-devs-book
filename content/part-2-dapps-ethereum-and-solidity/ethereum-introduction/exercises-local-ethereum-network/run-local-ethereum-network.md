# Exercises: Running a Local Ethereum Network

In this exercise, we will use **geth** to run a local Ethereum network
in class. In the beginning, we will create two Nodes, which work on
separate chains, then connect them and then see which chain will become
the main chain. After that in class, we will connect with each other for
more experience and fun!

# Setting up two Chains

To start with, we will run two nodes on different chains.

First:

1.  **Create** two directories in a convenient place for you. **Open two
    terminals in both of the directories.**

2.  Then, **Run Geth** on testnet with specific port and IPC path in
    order to divide the two chains, and **open** the Geth JavaScript
    console.

Alice\'s Chain:

  -------------------------------------------------------------------------
  geth \--testnet \--datadir=. \--port=30303 \--ipcpath=alice.ipc console
  -------------------------------------------------------------------------

![](/assets/exercise-running-local-ethereum-network-01.png)

Bob\'s Chain:

  -----------------------------------------------------------------------
  geth \--testnet \--datadir=. \--port=30304 \--ipcpath=bob.ipc console
  -----------------------------------------------------------------------

![](/assets/exercise-running-local-ethereum-network-01.png)

3.  Now, let\'s create two accounts:

Alice\'s Chain:

![](/assets/exercise-running-local-ethereum-network-01.png)

Bob\'s Chain:

![](/assets/exercise-running-local-ethereum-network-01.png)

4.  Let\'s start the miner on the first node:

Alice\'s Node:

  ---------------
  miner.start()
  ---------------

![](/assets/exercise-running-local-ethereum-network-01.png)

5.  Let\'s wait one minute to make one of the chains deliberately longer
    than the other:

Bob\'s Node:

![](/assets/exercise-running-local-ethereum-network-01.png)

Add peers
---------

Now that the two Nodes have mined some blocks on different chains, it is
time to connect them!

6.  But before we add peers, let's see how much blocks were mined and
    ETH have the two addresses been rewarded so far:

  eth.blockNumber
  --------------------------------------------
  web3.fromWei(eth.getBalance(eth.coinbase))

Alice's Chain:

![](/assets/exercise-running-local-ethereum-network-01.png)

Bob\'s Chain:

![](/assets/exercise-running-local-ethereum-network-01.png)

We can see that Alice's Chain is almost 3 times longer than Bob's.

7.  Now it's time to add Alice's Node as a peer to Bob's Node. In order
    for this to happen, we will need Alice's URI. For that puprose, we
    will use the **"admin"** command to see additional information about
    her node:

![](/assets/exercise-running-local-ethereum-network-01.png)

As we can see Alice's Node has no peers so far. In order to connect to
another node, we will need the **ethereum node URI**. The **enode
format** is (\<node-id\>@\<IP\>:\<PORT\>). Let's **copy** it.

Now, it is time Bob to add her as a peer. For example:

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  admin.addPeer(\"enode://8603db1d5f9552b4b604cea70c50ef97b753e2c227adfe60b55cb9549dd1a2214c021d062f780835969b8f7aa614760c7b619de787b0f618745cb80178a21219@\[::\]:30303\")
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![](/assets/exercise-running-local-ethereum-network-01.png)

What see is that when Bob\'s Node added Alice\'s Node as a peer, Bob\'s
Node preferred the **longest chain** based on the most work measured in
terms equivalent to the sum of the difficulty of all the blocks. Due to
the difference of the chains since the genesis block, Bob\'s Ethers
disappeared, because they were on a separate chain.

When we start Bob\'s miner again:

![](/assets/exercise-running-local-ethereum-network-01.png)

Bob\'s peers:

![](/assets/exercise-running-local-ethereum-network-01.png)

Alice\'s peers:

![](/assets/exercise-running-local-ethereum-network-01.png)

What we see in Alice\'s Node while Bob\'s Miner is working:

![](/assets/exercise-running-local-ethereum-network-01.png)

Connect with your colleagues in class
-------------------------------------

Now, it is time to connect in class. For that purpose, we will only make
a slight change when adding peers to our node. What we need to change is
the IP address from the default given with the Local IP Address of the
colleague\'s.

For example, the enode URI is:

enode://8c27041e4f33fdf0b7a373cf6c66ef8e3b14232c7116bb02a4b9bb2c59d3654b091597a16ed3dcd2755770e039d4cb4164e5576025993168a48775ba3f5eb7b1@**192.168.164.224**:30303

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  admin.addPeer(\"enode://8c27041e4f33fdf0b7a373cf6c66ef8e3b14232c7116bb02a4b9bb2c59d3654b091597a16ed3dcd2755770e039d4cb4164e5576025993168a48775ba3f5eb7b1\@192.168.164.224:30303\")
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

What to Submit?
===============

Create a **zip file** (e.g.
**yourUsername-running-local-ethereum-network.zip**) holding the
screenshots of how you make the two nodes on your laptop, how you
connect them and what happens with the chains, and then how you add some
of your colleagues as peers and what happens to your chain.

Submit your **zip** file as **homework** at the course Web site.
