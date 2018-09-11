# Exercises: Buy an Article using Lightning Mobile Application

The goal of this exercise is to play with the Lightning Network on the
Bitcoin Testnet and make some off-chain transactions. For this purpose,
we will use the Lightning Mobile Application and buy an article from
Yalls (<https://yalls.org>). We will create a node in the Lightning
Network Testnet, open channels with other nodes and create off-chain
transactions.

![](/assets/excercise-using-the-lightning-network-mobile-01.png)

Setup the Lightning Mobile Application
--------------------------------------

1.  Go to
    <https://play.google.com/store/apps/details?id=fr.acinq.eclair.wallet&hl=en>
    and install the app.

    Notice : Only android version exists for now.

    ![](/assets/excercise-using-the-lightning-network-mobile-011.png)

2.  **Read** and agree on the terms and conditions

    ![](3. Excercise-Using-the-Lightning-network-mobile/media/image3.png)

<!-- -->

2.  **Create** or **import** a wallet. If you have a wallet with test
    bitcoins you can import it and you will skip the faucet part.

    ![](/assets/excercise-using-the-lightning-network-mobile-013.png)

3.  If you choose "**Create new wallet**" you will see 24 words mnemonic
    phrase which you need to write somewhere or you can skip it, because
    the funds are in the Testnet.

![](/assets/excercise-using-the-lightning-network-mobile-015.png)

5.  Now you have a bitcoin Testnet wallet. Copy your wallet address and
    go to **Bitcoin Testnet Sandbox Faucet**
    (<https://testnet.manu.backend.hamburg/faucet>). Paste your address
    and click **\[Give me some coins\]**. If everything is okay, a
    message with the transaction ID will appear. You can check your
    transaction in the Testnet Bitcoin explorer
    (<https://testnet.blockchain.info/>).

    ![](/assets/excercise-using-the-lightning-network-mobile-016.png)

6.  Once the Eclair App is synchronized, your balance will appear in the
    app.

![](/assets/excercise-using-the-lightning-network-mobile-017.png)

Opening a payment channel
-------------------------

1.  The rest of the exercise is mainly playing inside the application.
    However, this is where you will likely experience the minor hiccups
    the alpha software still has.

2.  In order to get the required information to create a channel, we
    will go to the **Lightning Network Explorer \[TESTNET\]**
    ([**https://explorer.acinq.co**](https://explorer.acinq.co)) and
    pick a node. For this part of the exercise, we will create a payment
    channel with one of the most famous node in Testnet LN, called
    **endurance.** In the top **right corner**, type "endurance" in the
    search box and click on it. You can see the Public Key and IP of the
    node, required to open a channel.

![](/assets/excercise-using-the-lightning-network-mobile-018.png)

3.  Click **\[Scan node URI\]**, choose an amount of BTCt to put in the
    channel (the minimum is 0.001 and the maximum is 0.16 ) and click
    **\[Open\]**.

    Note: **Opening** and **closing** a channel are transactions stored
    on the main blockchain.\
    Note: You must **wait** 15 -- 25 minutes for opening a channel.

    ![](/assets/excercise-using-the-lightning-network-mobile-02.png)

4.  In the **\[Channels\]** section a **pending-open** channel will
    appear. After 20 minutes the channel will be with status
    "**normal**"

You have several statuses for a channel:

-   **GOSSIPING -** means that you are connected to a peer but there is
    no payment channel yet.

-   **OPENINGD -** means that lightning\_openingd is negotiating channel
    opening.

-   **CHANNELD\_AWAITING\_LOCKIN -** means that lightning\_channeld is
    waiting until the minimum number of confirmation on the channel
    funding transaction.

-   **CHANNELD\_NORMAL -** means your channel is operating normally.

-   **CHANNELD\_SHUTTING\_DOWN** - means one or both sides have asked to
    shut down the channel, and we\'re waiting for existing HTLCs to
    clear.

-   **CLOSINGD\_SIGEXCHANGE -** means we\'re trying to negotiate the fee
    for the mutual close transaction.

-   **CLOSINGD\_COMPLETE -** means we\'ve broadcast our mutual close
    transaction (which spends the funding transaction) but haven\'t seen
    it in a block yet.

-   **FUNDING\_SPEND\_SEEN -** means we\'ve seen the funding transaction
    spent.

-   **ONCHAIN** - means that the lightning\_onchaind is tracking the
    onchain closing of the channel.

![](/assets/excercise-using-the-lightning-network-mobile-04.png)

Buy an article from Yalls
-------------------------

1.  Go to <https://yalls.org/>, pick an article and click **\[Continue
    Reading\]:**

    ![](/assets/excercise-using-the-lightning-network-mobile-05.png)

2.  A payment request and a peer URI will appear. You can use your
    camera to scan and make a payment.
    ![](/assets/excercise-using-the-lightning-network-mobile-06.png)

3.  Then, **scan** the payment request in the Eclair App and pay the
    invoice.
    ![](/assets/excercise-using-the-lightning-network-mobile-08.png)

4.  Message "**Payment sent**" appears. When we return to the article,
    it will be already "**unlocked**":

    ![](/assets/excercise-using-the-lightning-network-mobile-09.png)

5.  If you go back to **\[Transaction History\]** tab in the Eclair App,
    you will see a list of all your transactions. Note that some
    transactions have different logos. The ones with the Bitcoin logo
    are transactions on the Bitcoin blockchain, and the others with the
    lightning logo are **off-chain transactions**. Check if a lightning
    transaction exists in the Bitcoin explorer.

    ![](/assets/excercise-using-the-lightning-network-mobile-010.png)

What to Submit?
===============

Create a **zip file** (e.g.
**username-buy-article-lighting-mobile-app-exercise.zip**) holding the
screenshots with your transactions.

Submit your **zip** file as **homework** at the course Web site.
