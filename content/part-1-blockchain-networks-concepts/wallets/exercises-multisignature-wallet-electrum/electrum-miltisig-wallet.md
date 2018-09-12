# Exercises: Creating and Spending from a Multi-Signature Wallet with Electrum

During the exercise you will **learn** how to make **Multi-Signature
Bitcoin wallet** and how to spend from it. This exercise requires 3-4
people in a team to complete it. For this purpose, we will use the
**Electrum wallet**. Please download Electrum from
<https://electrum.org/#download>.

Run Electrum Testnet App
------------------------

-   **Mac OS** Users

    -   Open **Terminal**

    -   **Execute** " open -n /Applications/Electrum.app/ \--args
        --testnet "

![](/assets/exercises-electrum-multisig-wallet-030.png)

-   **Windows** Users -- **If you have 'Electrum Testnet' icon, just
    doubleclick it and go to Step 2.**

    -   Right-click on the 'Electrum' app icon Properties

        ![](/assets/exercises-electrum-multisig-wallet-031.png)

    -   In the 'Target' field append **\--testnet after the columns**
        (see the picture example above)

Standard Wallets 
-----------------

> **This step is compulsory for each member to go through it
> individually.**

When you open Electrum App, a setup wizard will show up.

1.  Click on **"Auto Connect"** and click **"Next"**

    ![](/assets/exercises-electrum-multisig-wallet-032.png)

2.  Choose Wallet name and click
    **"Next"**![](/assets/exercises-electrum-multisig-wallet-029.png)

4.  Choose **"Create a new seed"** and click "**Next"**

    ![](/assets/exercises-electrum-multisig-wallet-027.png)

5.  Choose **"Standard"** seed type and click "**Next"**

    ![](/assets/exercises-electrum-multisig-wallet-026.png)

6.  **Read Carefully** the instructions about your seed! **Write down**
    your **seed** and click "**Next"**

    ![](/assets/exercises-electrum-multisig-wallet-01.png)

7.  Confirm your seed and click **"Next"**. **Never** **disclose** your
    **seed** to anyone else.

    ![](/assets/exercises-electrum-multisig-wallet-02.png)

8.  This step is optional. If you don't want your wallet to be
    encrypted, click
    **"Next"**.![](/assets/exercises-electrum-multisig-wallet-012.png)

9.  Please **wait** until electrum **generate** your **addresses** from
    the **given seed**

    ![](/assets/exercises-electrum-multisig-wallet-011.png)

10. Congratulations, you have created a **'Standard Wallet'** using
    Electrum App

    ![](/assets/exercises-electrum-multisig-wallet-09.png)

11. []{#obtain_pubkey .anchor}Now you need to obtain and **save your
    master public key**. You will **need** it for the next step when
    creating the **Multi-Signature wallet**.

    a.  For **Windows** users: click **"Wallet" "Information"**

> ![](/assets/exercises-electrum-multisig-wallet-010.png)

b.  For **Mac OS** users: click **"Wallet" "Master Public Keys"**

    ![](/assets/exercises-electrum-multisig-wallet-03.png)

Create Multi-Signature Wallet
-----------------------------

1.  Trigger the wallet creation wizard via file menu \> new/restore (for
    Mac users press ⌘N ), enter the desired wallet file name then click
    **"Next"**

> ![](/assets/exercises-electrum-multisig-wallet-08.png)

3.  Choose the Multi-Signature wallet depending on your team.

    a.  3 People - **3 cosigners** ,**2
        signatures**![](/assets/exercises-electrum-multisig-wallet-020.png)

4.  Now you need to **add** each **cosigner's** **Master Public Key**
    obtained from [**Step 2/11**](#obtain_pubkey).

    ![](/assets/exercises-electrum-multisig-wallet-025.png)

5.  After you add all the cosigners' Master Public Keys your
    **Multi-Signature** wallet will be **created**.

    ![](/assets/exercises-electrum-multisig-wallet-014.png)

Fund Your Multi-Signature Wallet
--------------------------------

1.  Go to the Bitcoin Testnet faucet:
    <https://testnet.manu.backend.hamburg/faucet>

2.  Copy your receiving address from Electrum Wallet.
    ![](/assets/exercises-electrum-multisig-wallet-015.png)

4.  After **clicking "Give Some Coins"** button you should have an
    **unconfirmed transaction** in the wallet under the **"History"
    tab**.

![](/assets/exercises-electrum-multisig-wallet-016.png)

Spend from the Multi-Signature Wallet
-------------------------------------

1.  Go to **"Send**" tab of the **Electrum App** and do the following:

    a.  paste a **receiving address**

    b.  set **amount** to be sent

    c.  adjust **fee** ( preferably click "Max" to ensure faster
        confirmation )

    d.  click **"Send"**

        ![](/assets/exercises-electrum-multisig-wallet-022.png)

2.  **Whenever** the transaction is **signed** by you, this window
    should appear.

    ![](/assets/exercises-electrum-multisig-wallet-023.png)

3.  In order for the transaction to be **broadcasted**, you need to save
    the file, and send it to the other **cosigners**.

    ![](/assets/exercises-electrum-multisig-wallet-019.png)

4.  To load and sign the transaction, go to **"Tools Load Transaction
    From file"** open the received transaction file

    e.  **Mac** Os User Interface

        ![](/assets/exercises-electrum-multisig-wallet-017.png)

    f.  **Windows** User Interface

        ![](/assets/exercises-electrum-multisig-wallet-04.png)

5.  Click **"Sign"** button. If the transaction is **already signed** by
    you the button will be **disabled**.

    ![](/assets/exercises-electrum-multisig-wallet-05.png)

6.  Once there are **enough signatures** gathered, the **"Broadcast"**
    button will become **enabled** and the transaction can be
    **broadcasted** to the network. Press **"Broadcast"** button to
    execute transaction.\
    ![](/assets/exercises-electrum-multisig-wallet-021.png)

7.  Congratulations! You have **successfully** spent assets from a
    Multi-Signature wallet.

    ![](/assets/exercises-electrum-multisig-wallet-024.png)

8.  In the receiver's wallet you should see the **unconfirmed**
    **pending** **transaction** from the Multi-Signature wallet.

    ![](/assets/exercises-electrum-multisig-wallet-018.png)

What to Submit?
===============

Submit as exercise outcome the **URL of your Transaction ID** in the
Bitcoin testnet network e.g.:

-   <https://www.blocktrail.com/tBTC/tx/813d29efd2a82409ccd06c23d95cf9bb324d123c0a8d5a3376bdfa73eea85036>

You should see some **BTC** in your balance, as well as some transaction
history of BTC transfers in the receiver's wallet.
