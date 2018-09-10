# Exercises: Playing with Ethereum Mist

In this exercise we shall install a **Mist** and **Geth** and will play
with them. We shall **create account**, **mine ethers** to it, **send
ethers** from one account to another.

-   [**Geth**](https://geth.ethereum.org) is the command line interface
    for running a **full Ethereum node** implemented in Go. It is one of
    the most popular Ethereum clients along with
    [**Parity**](https://www.parity.io). By installing and running Geth,
    you can take part in the Ethereum frontier live network and interact
    with it, e.g.

    -   Mine ethers

    -   Transfer funds between addresses

    -   Create contracts and send transactions

    -   Explore the block history

    -   and much, much more ...

-   [**Mist**](https://github.com/ethereum/mist) is a **GUI Ethereum
    client** and **wallet** software which provides a nice-looking GUI
    for Geth. It is an Electron-based JavaScript desktop application (a
    desktop hybrid application with a Web interface).

Download and Install Geth
-------------------------

First, let's **install a Geth** on your local machine.

1.  Go to <https://geth.ethereum.org/downloads/> and choose one of the
    following files.

![](/assets/exercises-playing-with-mist-01.png)

2.  Then start the downloaded file and **Accept** the agreement.

![](/assets/exercises-playing-with-mist-012.png)

3.  Choose the **Geth** and **Development tools** components and click
    \[**Next**\].

![](/assets/exercises-playing-with-mist-023.png)

4.  Select the location where you want to install Geth and click
    \[**Next**\].

![](/assets/exercises-playing-with-mist-025.png)

5.  After it is completed, click \[**Close**\].

![](/assets/exercises-playing-with-mist-026.png)

Play with Geth
--------------

**Run Geth** and select the **Ropsten testnet** and open the JavaScript
**console**:

  -------------------------
  geth \--testnet console
  -------------------------

![](/assets/exercises-playing-with-mist-027.png)

At the console, you can interactively execute commands, just as in the
JavaScript REPL in Node.js.

Display the available **wallets** and **accounts**. Type the following
command at the console:

  ----------
  personal
  ----------

![](/assets/exercises-playing-with-mist-028.png)

Create a **new account** in your wallet (if you don't have already):

  -----------------------
  personal.newAccount()
  -----------------------

List all your accounts **again** after you have created a new account:

  ----------
  personal
  ----------

Start **CPU mining** inside your local Ethereum node:

  ---------------
  miner.start()
  ---------------

Note that the **mining will happen in your local node only**, because it
is not connected to any existing networks. The miner will **mine 5 ETH
per \~ 12 seconds** (stored in your first account in your local wallet).
If you want your node to process transactions, the miner should be
running continuously. The miner's activity looks like this:

![](/assets/exercises-playing-with-mist-029.png)

Check the **account balance** to see how much ETH you have mined:

  --------------------------------------------
  web3.fromWei(eth.getBalance(eth.coinbase))
  --------------------------------------------

![](/assets/exercises-playing-with-mist-030.png)

Download and Install Mist
-------------------------

Now install **Mist** -- the official Ethereum **GUI client**, that
attaches to your Geth and interacts with it.

1.  Go to <https://github.com/ethereum/mist/releases/> and download one
    of the following files:

![](/assets/exercises-playing-with-mist-02.png)

2.  Run the downloaded file and **Accept** the license agreement.

![](/assets/exercises-playing-with-mist-03.png)

3.  Select the location where you want to install **Mist** and press
    \[**Next**\].

![](/assets/exercises-playing-with-mist-04.png)

4.  Select the location where the blockchain data will be stored and
    click \[**Install**\].

![](/assets/exercises-playing-with-mist-05.png)

5.  After the installation is completed, click \[**Close**\].

![](/assets/exercises-playing-with-mist-06.png)

Start Geth and Mist and Create New Account
------------------------------------------

1.  Open command prompt and **start Geth** on the **testnet** with
    interactive **console**:

  -------------------------
  geth \--testnet console
  -------------------------

![](/assets/exercises-playing-with-mist-07.png)

2.  Start **Mist**. It will automatically connect to the local **Geth**
    node. Press \[**Launch Application**\].

![](/assets/exercises-playing-with-mist-08.png)

3.  You will see the following window. Go to the \[**Wallets**\] tab.
    Your accounts will appear. Press \[**Add Account**\] to create a new
    account. You will need at least two accounts in your wallet in order
    to send transaction between them.

![](/assets/exercises-playing-with-mist-09.png)

4.  Press \[**Create new account**\].

![](/assets/exercises-playing-with-mist-010.png)

5.  Enter a password you want and press \[**OK**\].

![](/assets/exercises-playing-with-mist-011.png)

6.  You should see the following window after successful account
    creation.

![](/assets/exercises-playing-with-mist-013.png)

Your wallet should now hold at least **two accounts**:

![](/assets/exercises-playing-with-mist-014.png)

Mine and Send Between Accounts
------------------------------

When your Mist browser is started and connected to your local Ethereum
node, your mining is visualized in Mist.

1.  **Start the miner** in your Geth console with 2 threads (it is an
    optional parameter).

![](/assets/exercises-playing-with-mist-015.png)

2.  You can look at the Geth console that the miner is started mining.

![](/assets/exercises-playing-with-mist-016.png)

3.  After a while, you will see additional **5.00 ethers** at your main
    account.

![](/assets/exercises-playing-with-mist-017.png)

4.  Copy the **address** of **Account 2** that you created previously:

![](/assets/exercises-playing-with-mist-018.png)

5.  Go to \[**Send**\] tab, paste the **Account 2** address and enter
    amount to send, e.g. **2.5 ethers**.

![](/assets/exercises-playing-with-mist-019.png)

6.  You can adjust the miner's fee for faster (and more expensive)
    transaction or slower (and cheaper) transaction. Finally click
    \[**Send**\].

![](/assets/exercises-playing-with-mist-020.png)

7.  Enter your **sender account password** and click \[**Send
    Transaction**\].

![](/assets/exercises-playing-with-mist-021.png)

8.  After the successful transaction you should see the following
    window.

![](/assets/exercises-playing-with-mist-022.png)

See the **Geth** console that runs the miner. It should hold a block
with 1 transaction (your transaction you just sent):

![](/assets/exercises-playing-with-mist-024.png)

What to Submit?
===============

Submit as exercise outcome your "**Main account" and "account 2"
addresses, screenshots of the ether balances of the addresses**.
Examples:

![](/assets/exercises-playing-with-mist-022.png)
