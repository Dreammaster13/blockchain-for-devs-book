# Exercises: Buy and Send ERC20 Tokens

In this exercise we will play with **ERC20 tokens**. We shall unlock our
wallet software, send transactions, watch the transaction processing and
buy, sell and send/receive crypto-tokens (ERC20 tokens).

For this exercise we shall use Web-based crypto-wallet software called
**MyEtherWallet** (**MEW**), which behaves like locally installed
Ethereum crypto wallets, but is accessible through the Web, without any
installation.

-   MyEtherWallet is a **client-side wallet software**. It does not
    store your private keys, neither sends them at the server-side.
    Keeping your keys is a secure place is your obligation.

-   MEW connects to the Ethereum blockchain through **REST API** (using
    client-side AJAX calls from JavaScript). The MyEtherWallet API is
    officially documented here: <https://www.myetherapi.com>.

-   You can create / export / import **wallet keys**, sign and **send
    transactions** and **browse the blockchain**.

-   MEW works with the **main** (production) Ethereum network, as well
    as with testing networks (**testnets**) like Ropsten, Kovan and
    Rinkeby.

Buy ERC20 Tokens
----------------

The next thing to do is to buy some **ERC20 tokens**.

**Tokens** are digital assets hold in a **smart contract**. Typically,
**token sale events** (also wrongly known as ICO) sale tokens to people
who send ETH and get some tokens in the contract. Most token sale events
use the [ERC20 token
standard](https://theethereum.wiki/w/index.php/ERC20_Token_Standard) in
their token sale smart contracts.

Note that **tokens are different than coins**:

-   **Coins** (like Bitcoin, Ethereum and Dash) are digital currency
    assets hold by network accounts. Coin balances are stored in network
    addresses.

-   **Tokens** (like Augur and EOS) are balances stored in a certain
    smart contract for certain network address. Token operations (like
    send and receive tokens) are done through the contract address.

Let's get some tokens now.

1.  Go to **"Contracts"** tab.

2.  You can add the contract address and ABI/JSON Interface or select it
    from the drop-down menu from right.

![](/assets/exercises-buy-and-send-erc20-tokens-01.png)

3.  We will select from the drop-down menu and access it:

![](/assets/exercises-buy-and-send-erc20-tokens-04.png)

4.  Now you will see the functions of the contract and select the
    **"buyTokenPay"** to buy tokens from the contract and click
    **Write**.

![](/assets/exercises-buy-and-send-erc20-tokens-05.png)

![](/assets/exercises-buy-and-send-erc20-tokens-06.png)

5.  Write **1 ether** for amount to send. The **Gas Limit** is
    calculated automatically. You can write it manually and **Generate
    Transaction**. Then click **"Yes, I am sure! Make transaction"**

![](/assets/exercises-buy-and-send-erc20-tokens-07.png)

6.  Now go to view your wallet info. Click "**Load Tokens**" (you can
    add the tokens by yourself by clicking "Add Custom Token").

![](/assets/exercises-buy-and-send-erc20-tokens-08.png)

7.  You will see the tokens you've bought:

![](/assets/exercises-buy-and-send-erc20-tokens-09.png)

Congrats, now you have 0.1 PLASMA tokens!

Send Tokens to Another Address
------------------------------

1.  Get someone's address from the class and send him/her 0.05 PLASMA
    tokens.

2.  Go to the **"Send Ethers & Tokens"** tab and unlock your account
    with the **JSON file**. Put the **address** of your mate and the
    **amount** you want to send. The **Gas Limit** is the default one.
    Generate the transaction. Then click **Send Transaction.**

3.  Click **"Load Tokens"** to see the PLASMA token.

![](/assets/exercises-buy-and-send-erc20-tokens-010.png)

4.  Do the same step from **exercise 3**. Sending tokens is like sending
    ethers.

![](/assets/exercises-buy-and-send-erc20-tokens-011.png)

5.  Go to the wallet info and you should have 0.05 PLASMA tokens, if
    everything was successful.

![](/assets/exercises-buy-and-send-erc20-tokens-02.png)

Congrats, you've send 0.05 PLASMA tokens to your mate!

What to Submit?
===============

Submit as exercise outcome the **URL of your Ethereum address** in the
Ropsten network at EtherScan, e.g.:

-   <https://ropsten.etherscan.io/address/0xb97e993872a903850c07fbd999a6e750963ef195>

You should some **tokens** in your balance, as well as some transaction
history of token transfers. Examples:

![](/assets/exercises-buy-and-send-erc20-tokens-03.png)