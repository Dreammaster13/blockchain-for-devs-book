# Exercises: Buy and Sell Bitcoins on the Hodl Hodl p2p Exchange

In this Exercise we are going to be learning how to sell bitcoins with
Hodl Hodl. Hodl Hodl is a P2P cryptocurrency exchange that allows users
to trade directly with each other and it doesn\'t hold user funds -
locking it in multisig escrow instead - which minimizes the
possibilities of cryptocurrency theft and reduces trading time. Because
Hodl Hodl does not hold any money (neither cryptocurrency, nor fiat) it
is not subject to complex compliance procedures. All trades happen
directly between users\' cryptocurrency wallets.

In this exercise we will sell testnet bitcoins using Electrum wallet and
testnet version of Hodl Hodl.

In this exercise we use Ubuntu 16.04.3.

Install Testnet Electrum Wallet and take some Bitcoins
------------------------------------------------------

1.  If you already have account with some testnet Bitcoins you can just
    skip this part. In other way continue reading. Open **terminal** and
    **install Electrum**. First, we need to install dependencies.

  -------------------------------------------------------------------
  sudo apt-get install python3-setuptools python3-pyqt5 python3-pip
  -------------------------------------------------------------------

![](/assets/exercises-hodlhodl-01.png)

2.  Then **install Electrum**. 

  -----------------------------------------------------------------------------
  sudo pip3 install https://download.electrum.org/3.1.1/Electrum-3.1.1.tar.gz
  -----------------------------------------------------------------------------

![](/assets/exercises-hodlhodl-012.png)

3.  Now we need to setup Electrum to work in testnet. We will create
    shortcut in desktop. First open **nano** and create shortcut file.

  ----------------------------------
  nano \~/Desktop/electrum.desktop
  ----------------------------------

![](/assets/exercises-hodlhodl-023.png)

4.  Next write the following commands in the file.

+----------------------------+
| > \[Desktop Entry\]        |
| >                          |
| > Type=Application         |
| >                          |
| > Name=Electrum Testnet    |
| >                          |
| > Exec=electrum \--testnet |
| >                          |
| > Icon=electrum            |
+----------------------------+

![](/assets/exercises-hodlhodl-034.png)

Save the file. Press "**ctrl+x**" and next press "**y**" for yes.

5.  Now if you start the shortcut the precautionary message will appear.

    ![](/assets/exercises-hodlhodl-059.png)

8.  Now double click on shortcut and start the program. Choose auto
    connect.

    ![](/assets/exercises-hodlhodl-061.png)

10. Next choose what type of wallet you want to create. We choose
    **standard wallet**.

    ![](/assets/exercises-hodlhodl-02.png)

11. Now we need to choose the **seed type**. For this exercise the
    standard is ok.

    ![](/assets/exercises-hodlhodl-06.png)

15. Now the wallet is ready. Let\`s check the working network. Click on
    the green circle, server and nodes must work on testnet.

    ![](/assets/exercises-hodlhodl-07.png)

16. Now we must get some test coins. Go to receive section and copy the
    **address**.

    ![](/assets/exercises-hodlhodl-08.png)

17. If you want, before open the faucet you can change the **base unit**
    from mBTC to BTC.

    ![](/assets/exercises-hodlhodl-09.png)

18. Go to <https://testnet.manu.backend.hamburg/faucet> and paste
    address from wallet.

    ![](/assets/exercises-hodlhodl-010.png)

19. Open the wallet and check the address. Test coins must be there or
    on the way to you address.

    ![](/assets/exercises-hodlhodl-011.png)

Now when we have test Bitcoins it\`s time to open the Hodl Hodl and sell
some coins. 

Sell Bitcoins with Hodl Hodl
----------------------------

1.  Go to <https://hodlhodl.com/> and choose **testnet.**

    ![](/assets/exercises-hodlhodl-013.png)

2.  Now we are in HodlHodl testnet and can learn how to use the exchange
    with test coins. let\`s register account.

    ![](/assets/exercises-hodlhodl-014.png)

3.  Register the account. Enter your email, name, timezone, password
    etc.

    ![](/assets/exercises-hodlhodl-018.png)

7.  And click on **Sell bitcoins**. Here you can see the offers from
    other people. The filter offers section give you option to find
    easily suitable offers. Down the list is the offer from elvie-bot.
    He wants to buy bitcoins for 1000 USD. The payment method is in
    person. Elvie-bot is HodlHodl bot and we can use his offer and even
    himself to train.\
    ![](/assets/exercises-hodlhodl-019.png)

8.  Now open one more window with HodlHodl testnet and enter in the
    **elvie-bot account**.\
    All **HodlHodl bots** have emails with domain **\@hodlhodl.com** and
    password is always: **password**.\
    ![](/assets/exercises-hodlhodl-022.png)

11. Now before continue we must set your account info. Open **trading
    settings** in your account.\
    ![](/assets/exercises-hodlhodl-024.png)

12. You must enter the **working account** for HodlHodl. Open **Electrum
    wallet** and copy the еthereum **test account we created early**.\
    ![](/assets/exercises-hodlhodl-025.png)

13. **Paste** the address in your HodlHodl profile and click on **Save
    Changes**.\
    ![](/assets/exercises-hodlhodl-027.png)

15. Now let\`s return to the buying offer. We have option to sell
    bitcoins with value **between 500 and 1000 USD**. We want **500
    USD** and for them we must send **0.50150451 BTC**. Down below we
    must choose the **Payment method** and write details and comments.
    After all is filled up click on "**Accept offer and create
    contract**" button.\
    ![](/assets/exercises-hodlhodl-028.png)

16. Contract has been **successfully created**. The other side receive
    message for **new order**.\
    ![](/assets/exercises-hodlhodl-029.png)

17. The window of buyer and the window of seller are looking very
    similar. The two sides have 1 hour to finish the deal. Here is the
    address in which you must transfer the coins. The coins will stay in
    **special multisig escrow address** until the deal is finish and two
    sides received their money and coins.\
    ![](/assets/exercises-hodlhodl-030.png)

18. To be able to make the transfer, you must first set a **payment
    password**. Click on the "**Create** **payment password"** button.\
    ![](/assets/exercises-hodlhodl-031.png)

19. Enter the password (min. 10 symbols). This password serves as a
    private key for your unique multisig deposit address. **If you
    forget this password Hodl Hodl will not be able to reset and change
    it because it IS NOT stored on exchange server**. Hodl Hodl don\`t
    holding your funds. You are trading directly with your counterparty.
    **Hodl Hodl exchange only holds one-out-of-two keys to the multisig
    escrow**, which ensures safe trading for both buyers and sellers.
    Without payment password you can\`t take the funds locked in ongoing
    contracts. When you are ready click on the "**Create** **payment
    password"** button.\
    ![](/assets/exercises-hodlhodl-033.png)

21. Now we have all necessary information to make the payment. You must
    send exactly 0.50150451 BTC to given address.\
    ![](/assets/exercises-hodlhodl-035.png)

22. Now open your Electrum wallet. Paste the **address** and the
    **amount** and click "**Send**".\
    ![](/assets/exercises-hodlhodl-038.png)

25. The funds are locked in escrow. Every side can check the transaction
    info by click on the **transaction id** link.\
    ![](/assets/exercises-hodlhodl-040.png)

27. Now is turn to elvie-bot to made the payment. In this case the
    payment method is **in person** so let\`s assume the payment is
    done. Elvie-bot must click on the "**I\`ve sent the payment
    button**".\
    ![](/assets/exercises-hodlhodl-041.png)

28. When the payments are done we can **chat with other side**. Let\`s
    say to Elvie-bot that "Everything is ok" and Elvie-bot can answer
    "OK". In the final we can "**Release deposit**".\
    ![](/assets/exercises-hodlhodl-043.png)

30. When the deal is done each side can rate the other and write a
    review.

    ![](/assets/exercises-hodlhodl-044.png)

Creating Sell Offer with Hodl Hodl
----------------------------------

1.  First enter in your account. Then go to "**Sell bitcoins**" and
    "**Add offer**".

    ![](/assets/exercises-hodlhodl-046.png)

2.  In the Create new BTC offer choose the "**sell bitcoin**". Then
    choose the country. From this choice depends the payment methods
    down below.

    ![](/assets/exercises-hodlhodl-047.png)

3.  The next section is Price. We can choose fixed price or price from
    exchange. In this example we will choose Bitstamp. Payment currency
    will be USD and we wand 1% premium over Bitstamp price.

    ![](/assets/exercises-hodlhodl-048.png)

4.  Next is the **amount measured in currency**. We want amount between
    10 and 5000 USD.\
    **First-trade limit** enforces restrictions in case we don\`t know
    the other side and this is our first trade with them. In this case
    we show trust and let max limit to be 5000.

    ![](/assets/exercises-hodlhodl-049.png)

5.  In down below we must set how many **confirmations** wants to
    receive. The more confirmations decrease the risk our transaction
    get into the block in the abolished part of blockchain. This can
    happen if two miners simultaneously mined two different blocks and
    then the longest blockchain will be the winner. Three confirmations
    are ok in most cases.\
    Then are the Time constraints. We must foresee the long enough
    period, because after that time period the deal will be canceled.

    ![](/assets/exercises-hodlhodl-050.png)

6.  In the payment methods we choose varied option and write
    instructions and comments.\
    When all information is filled up check **published** check box to
    publish offer and click **Save.**

    ![](/assets/exercises-hodlhodl-051.png)

7.  And our offer to sell bitcoins is ready. We can edit, unpublish or
    delete it if we want.

    ![](/assets/exercises-hodlhodl-053.png)

Creating Buy Offer 
-------------------

1.  The principle is the same but this time we are in the role of buyer.
    For example: in the **Price** this time we wand 1% premium **under**
    Bitstamp price.

    ![](/assets/exercises-hodlhodl-054.png)

2.  This time we will send coins and receive money. So, In the payment
    methods we specify the method with which we are **willing to receive
    money**.\
    After all is filled up we must check **Published** check box and
    click **Save**.

    ![](/assets/exercises-hodlhodl-058.png)

5.  Follow the Described Steps
    --------------------------

Your task is follow the tutorial described above and perform the
experiments.

1.  Create buy and sell offers.

2.  Buy and sell coins from your colleges offers.

What to Submit?
===============

Create a **zip file** (e.g. **your-name-hodlhodl-exercise.zip**) holding
the screen shots with your deals.

Submit your zip file as **homework** at the course Web site.
