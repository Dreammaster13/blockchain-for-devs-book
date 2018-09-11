# Exercises: Playing with the Zcash Testnet

Using the Zcash Faucet, Send Anonymous Transactions

**Zcash** is a private cryptocurrency that supports transparent and
shielded transactions. Before you acquire some Zcash, you\'ll want to
make sure that you have a wallet set up to store it. You can download
the official Zcash client or use a third-party application to manage
your funds.

Download and Install ZCash-Related Packages
-------------------------------------------

1.  Open terminal on Linux and start installing the packages.

2.  First install the following dependency so you can talk to our
    repository using HTTPS:

    ![](/assets/exercise-zcash-testnet-faucet-send-transactions-01.png)

3.  Then add the Zcash master signing key to apt\'s trusted keyring
    (Fingerprint: F1E2 1403 7E94 E950 BA85 77B2 63C4 A216 9C1B 2FA2):

![](/assets/exercise-zcash-testnet-faucet-send-transactions-026.png)

5.  Now that Zcash is installed, run this command to download the
    parameters used to create and verify shielded transactions:

![](/assets/exercise-zcash-testnet-faucet-send-transactions-028.png)

Run the ZCash Daemon and Sync the Testnet
-----------------------------------------

6.  You will need to create a **.zcash** directory in your user home
    root.

7.  Notice: Change user abadzhievltd whit your username.

![](/assets/exercise-zcash-testnet-faucet-send-transactions-031.png)

10. Now we need to add network(testnet, mainnet) and node. For testnet
    write **testnet=1** and for mainnet **mainnet=1**.

11. We will use nano to edit the file which is linux terminal editor.

![](/assets/exercise-zcash-testnet-faucet-send-transactions-02.png)

12. In this file we have rpcuser and rpc password and we need to add
    node and network.

![](/assets/exercise-zcash-testnet-faucet-send-transactions-04.png)

Afterwards you need to press **Ctrl + Y** (for Yes) and Enter for the
same name.

![](/assets/exercise-zcash-testnet-faucet-send-transactions-05.png)

13. Once you\'ve configured your zcash.conf file, you can start the
    zcash daemon.

![](/assets/exercise-zcash-testnet-faucet-send-transactions-06.png)

14. You\'ll have to wait for the blockchain to sync the first time you
    start it up. Once you\'ve synced to the current blockheight, you can
    start using the zcash-cli to send and receive Zcash transactions!

![](/assets/exercise-zcash-testnet-faucet-send-transactions-09.png)

Create a Shielded Address
-------------------------

17. Get new Shielded testnet address with the command **zcash-cli
    z\_getnewaddress**, but if you want your address to be transparent
    write the following command **zcash-cli getnewaddress**

![](/assets/exercise-zcash-testnet-faucet-send-transactions-014.png)

Get Some Coins from the Faucet
------------------------------

20. Go to <https://faucet.testnet.z.cash> and paste one of the
    transparent addresses, e.g. **tmWKycLPfFjWYT87fZH4PcNybXdTLDFzowK**
    and Tap Faucet and you will receive 3 ZEC

![](/assets/exercise-zcash-testnet-faucet-send-transactions-015.png)

21. Go to <https://explorer.testnet.z.cash> and paste the transaction
    and you can see the Transaction Summary and Details

![](/assets/exercise-zcash-testnet-faucet-send-transactions-018.png)

Send a Confidential Transaction
-------------------------------

2.  Let\'s put the addresses in environment variables to avoid mistakes:

Notice : Use z-address from Z\_listaddresses command

![](/assets/exercise-zcash-testnet-faucet-send-transactions-021.png)

After waiting about **two minutes**, you can check to see if the
operation has finished and produced a result:

![](/assets/exercise-zcash-testnet-faucet-send-transactions-022.png)

5.  After waiting for the transaction to be mined, you can check the
    balance of the receiver if the 0.5 ZEC amount are at the address
    which you've sent them to:

![](/assets/exercise-zcash-testnet-faucet-send-transactions-024.png)

6.  You can use the transaction ID to see the transaction in the block
    explorer; note how in "public output" it says "0 ZEC", that the
    shielded address is not mentioned anywhere, and also note the
    transaction size (around 2kb):

    ![](/assets/exercise-zcash-testnet-faucet-send-transactions-025.png)

Notice: Please stop and delete your instance.\
Thank you.

What to Submit?
===============

Create a **zip file** (e.g. **your-name-zcash-cli.zip**) holding the
screenshots with your experiments. Make screenshots of the terminal.
Submit your **zip** file as **homework** at the course Web site.

