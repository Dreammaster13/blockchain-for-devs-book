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

![](/assets/exercises-playing-with-mist-01.png){width="6.72253280839895in"
height="2.232898075240595in"}

2.  Then start the downloaded file and **Accept** the agreement.

![](/assets/exercises-playing-with-mist-012.png){width="3.7227843394575677in"
height="2.5537937445319336in"}

3.  Choose the **Geth** and **Development tools** components and click
    \[**Next**\].

![](/assets/exercises-playing-with-mist-023.png){width="3.732250656167979in"
height="2.5687193788276463in"}

4.  Select the location where you want to install Geth and click
    \[**Next**\].

![](/assets/exercises-playing-with-mist-025.png){width="3.7864643482064744in"
height="2.606032370953631in"}

5.  After it is completed, click \[**Close**\].

![](/assets/exercises-playing-with-mist-026.png){width="3.7403608923884515in"
height="2.5413003062117236in"}

Play with Geth
--------------

**Run Geth** and select the **Ropsten testnet** and open the JavaScript
**console**:

  -------------------------
  geth \--testnet console
  -------------------------

![](/assets/exercises-playing-with-mist-027.png){width="7.2444444444444445in"
height="3.9944444444444445in"}

At the console, you can interactively execute commands, just as in the
JavaScript REPL in Node.js.

Display the available **wallets** and **accounts**. Type the following
command at the console:

  ----------
  personal
  ----------

![](/assets/exercises-playing-with-mist-028.png){width="6.892700131233596in"
height="3.768786089238845in"}

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

![](/assets/exercises-playing-with-mist-029.png){width="7.2444444444444445in"
height="3.759027777777778in"}

Check the **account balance** to see how much ETH you have mined:

  --------------------------------------------
  web3.fromWei(eth.getBalance(eth.coinbase))
  --------------------------------------------

![](/assets/exercises-playing-with-mist-030.png){width="7.2444444444444445in"
height="2.2729166666666667in"}

Download and Install Mist
-------------------------

Now install **Mist** -- the official Ethereum **GUI client**, that
attaches to your Geth and interacts with it.

1.  Go to <https://github.com/ethereum/mist/releases/> and download one
    of the following files:

![](/assets/exercises-playing-with-mist-02.png){width="4.531405293088364in"
height="3.4246161417322836in"}

2.  Run the downloaded file and **Accept** the license agreement.

![](/assets/exercises-playing-with-mist-03.png){width="3.460592738407699in"
height="2.3964402887139107in"}

3.  Select the location where you want to install **Mist** and press
    \[**Next**\].

![](/assets/exercises-playing-with-mist-04.png){width="3.4886679790026247in"
height="2.3896139545056867in"}

4.  Select the location where the blockchain data will be stored and
    click \[**Install**\].

![](/assets/exercises-playing-with-mist-05.png){width="3.5649398512685915in"
height="2.441852580927384in"}

5.  After the installation is completed, click \[**Close**\].

![](/assets/exercises-playing-with-mist-06.png){width="3.658270997375328in"
height="2.505786307961505in"}

Start Geth and Mist and Create New Account
------------------------------------------

1.  Open command prompt and **start Geth** on the **testnet** with
    interactive **console**:

  -------------------------
  geth \--testnet console
  -------------------------

![](/assets/exercises-playing-with-mist-07.png){width="7.2444444444444445in"
height="4.001388888888889in"}

2.  Start **Mist**. It will automatically connect to the local **Geth**
    node. Press \[**Launch Application**\].

![](/assets/exercises-playing-with-mist-08.png){width="4.464562554680665in"
height="2.6955850831146106in"}

3.  You will see the following window. Go to the \[**Wallets**\] tab.
    Your accounts will appear. Press \[**Add Account**\] to create a new
    account. You will need at least two accounts in your wallet in order
    to send transaction between them.

![](/assets/exercises-playing-with-mist-09.png){width="5.556027996500437in"
height="3.173196631671041in"}

4.  Press \[**Create new account**\].

![](/assets/exercises-playing-with-mist-010.png){width="4.267004593175853in"
height="3.9343897637795275in"}

5.  Enter a password you want and press \[**OK**\].

![](/assets/exercises-playing-with-mist-011.png){width="3.5836450131233595in"
height="3.304294619422572in"}

6.  You should see the following window after successful account
    creation.

![](/assets/exercises-playing-with-mist-013.png){width="5.023942475940507in"
height="1.4056157042869641in"}

Your wallet should now hold at least **two accounts**:

![](/assets/exercises-playing-with-mist-014.png){width="7.2444444444444445in"
height="3.2291666666666665in"}

Mine and Send Between Accounts
------------------------------

When your Mist browser is started and connected to your local Ethereum
node, your mining is visualized in Mist.

1.  **Start the miner** in your Geth console with 2 threads (it is an
    optional parameter).

![](/assets/exercises-playing-with-mist-015.png){width="1.6611111111111112in"
height="0.58209864391951in"}

2.  You can look at the Geth console that the miner is started mining.

![](/assets/exercises-playing-with-mist-016.png){width="6.148669072615923in"
height="2.7925995188101487in"}

3.  After a while, you will see additional **5.00 ethers** at your main
    account.

![](/assets/exercises-playing-with-mist-017.png){width="6.040651793525809in"
height="2.4418536745406825in"}

4.  Copy the **address** of **Account 2** that you created previously:

![](/assets/exercises-playing-with-mist-018.png){width="6.031405293088364in"
height="1.7240846456692913in"}

5.  Go to \[**Send**\] tab, paste the **Account 2** address and enter
    amount to send, e.g. **2.5 ethers**.

![](/assets/exercises-playing-with-mist-019.png){width="6.553792650918635in"
height="2.915657261592301in"}

6.  You can adjust the miner's fee for faster (and more expensive)
    transaction or slower (and cheaper) transaction. Finally click
    \[**Send**\].

![](/assets/exercises-playing-with-mist-020.png){width="5.805009842519685in"
height="2.727777777777778in"}

7.  Enter your **sender account password** and click \[**Send
    Transaction**\].

![](/assets/exercises-playing-with-mist-021.png){width="3.0085433070866143in"
height="2.97170384951881in"}

8.  After the successful transaction you should see the following
    window.

![](/assets/exercises-playing-with-mist-022.png){width="5.637490157480315in"
height="2.3075240594925632in"}

See the **Geth** console that runs the miner. It should hold a block
with 1 transaction (your transaction you just sent):

![](/assets/exercises-playing-with-mist-024.png){width="7.2444444444444445in"
height="3.204861111111111in"}

What to Submit?
===============

Submit as exercise outcome your "**Main account" and "account 2"
addresses, screenshots of the ether balances of the addresses**.
Examples:

![](/assets/exercises-playing-with-mist-022.png){width="5.083202099737533in"
height="2.0806452318460193in"}
