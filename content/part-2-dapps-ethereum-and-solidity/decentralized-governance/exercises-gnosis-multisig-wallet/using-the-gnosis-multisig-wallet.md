# Exercises: Using the Gnosis Multisig Ethereum Wallet

In this exercise we will play with the Gnosis Multisig Wallet app:
<https://wallet.gnosis.pm/> .We are going to **create** a
**multisignature wallet**, by configuring the owners of the wallet
contract and then **deploy** it on the Ethereum Testnet (Ropsten). After
the successful deployment, we will **send** couple of **transactions**
to and from the multisig wallet. For this purpose you will need **at
least 1 teammate** to create together the multisig wallet. You will also
need a Metamask with test account on Ropsten with some test ETH inside.

![](/assets/exercises-multi-signature-wallets-01.png)

Create a Multisignature Wallet and Define Owners
------------------------------------------------

> After you open <https://wallet.gnosis.pm> follow those simple steps:

1.  Click "**Add wallet now**", then click next with "**Create new
    wallet**" **checkbox** clicked:

> ![](/assets/exercises-multi-signature-wallets-09.png)

2.  After that you need to Configure the wallet contract:

    a.  Pick a "**Name**" of the contract

    b.  Set **Required Confirmations**- for security purposes, the more
        the confirmation the more irreversible the approved transaction
        will be. For the purpose of the tutorial you can add "**2**"
        required confirmations for faster approval time.

    c.  Set **daily limit** (ETH) by your choice.

    d.  Add the other **owners** of the **wallet** contract. Please note
        that your account will be automatically added. This is because
        Gnosis wallet app interacts with metamask, parity and mist and
        automatically adds you as an owner. Add at least 1 more owner in
        order to make the multisig wallet contract.

    e.  After everything is configured correct, click "Deploy with
        factory"

        ![](/assets/exercises-multi-signature-wallets-010.png)

    f.  After clicking "**Deploy with factory**", you need to submit the
        contract initialization transaction via metamask. The window
        below will popup automatically.

> ![](/assets/exercises-multi-signature-wallets-011.png)

g.  After the transaction has been confirmed by the network your
    **wallet** contract should be **listed** under "Wallets" tab of
    Gnosis Web Application.\
    ![](/assets/exercises-multi-signature-wallets-012.png)

    **Congratulations**! You have **successfully** **deployed** a
    multisig **wallet** **contract** on the Ethereum Testnet. Now let's
    try to Deposit and Withdraw ETH from the multisig contract.

    **Please Copy the address of the wallet contract and save it**. We
    will need it later.

Send Transaction
----------------

> In this section we will Deposit ETH to the contract and then withdraw
> them. We will **intentionally** **exceed** our **daily withdrawal
> limit** to show you that when the limit is exceeded, the
> **transaction** has to be **confirmed** from **all owners** in order
> to be **executed**.

1.  Click "**Deposit**" button under the "**Balance**" column of the
    "**Test**" wallet. Then **deposit** amount **bigger** **than the
    "Daily limit"** of the wallet.

> ![](/assets/exercises-multi-signature-wallets-013.png)

2.  []{#GasConfig .anchor}**Configure** the **Gas** and click "**Send
    Transaction**". Note that the **Gas price (GWei)** **should not be
    lower than 0,1**.\
    ![](/assets/exercises-multi-signature-wallets-014.png)

3.  []{#MetamaskSubmit .anchor}**Submit** the transaction once again
    from the Metamask Extension.

    ![](/assets/exercises-multi-signature-wallets-015.png)

4.  []{#withdraw .anchor}After the transaction has been **confirmed** by
    the network. Your wallet **balance** should be **updated**. Now go
    to the click the "**Withdraw**" button under "**Limit for today**"
    column of our wallet and **withdraw an amount lower than the Daily
    Limit**. Click "**Send Multisig Transaction**", and repeat steps
    [b.](#GasConfig) and [c.](#MetamaskSubmit)\
    ![](/assets/exercises-multi-signature-wallets-016.png)

5.  Note that Gnosis wallets requires signatures from all of the owner
    only when the amount exceeds the daily limit. After you have
    successfully withdrawn the amount from the contract wallet, now
    repeat again step [d.](#withdraw) , but this time withdraw amount
    that exceeds the daily limit.

6.  Now **click** on the **wallet** **name** to see all transactions
    connected to it.

    ![](/assets/exercises-multi-signature-wallets-012.png)

7.  As you can see the second transaction is **not** "**Executed**" .
    This is because of the fact that we exceeded the Daily Withdraw
    limit.

    ![](/assets/exercises-multi-signature-wallets-02.png)

Confirm Transaction when Daily Limit Exceeds
--------------------------------------------

> In this section we will sign and publish the transaction not Executed
> transaction, on behalf of the second owner.

1.  Open <https://wallet.gnosis.pm/> and click "**Add wallet now**"

    ![](/assets/exercises-multi-signature-wallets-03.png)

3.  Enter the contract name and address of the wallet contract and click
    "**OK**"

    ![](/assets/exercises-multi-signature-wallets-04.png)

4.  Now your wallet should appear in the "**Wallets**" tab. Click the
    wallet name ( in our case it is "Test" ) so you can get the list
    with all outgoing transactions from this wallet contract.

    ![](/assets/exercises-multi-signature-wallets-05.png)

5.  You can see the same transaction with **ID 1** that is not Executed,
    because it needs confirmation from each owner of the wallet. To
    confirm the transaction you need to click "**Confirm**" button.

    ![](/assets/exercises-multi-signature-wallets-07.png)

7.  **Congratulations**! You have successfully **confirmed** the
    transaction and make it **execute**.

    ![](/assets/exercises-multi-signature-wallets-08.png)

    **Please Note** that if there are **more than 2 owners**, each owner
    **has to Confirm** the needed transaction by **repeating**
    [Step2](#confirm-transaction-when-daily-limit-exceeds).
