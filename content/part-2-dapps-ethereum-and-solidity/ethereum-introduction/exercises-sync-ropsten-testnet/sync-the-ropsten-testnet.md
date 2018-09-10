# Exercises: Synchronize the Ropsten Testnet using the Geth Client

In this exercise, we will connect and sync the public Ropsten Testnet
using **"geth"** on our machine.

Starting the Client
-------------------

1.  **Create** a directory in a convenient place for you. Keep in mind
    that the Ropsten Chain data size is around 70GB now. **Go** to the
    directory and open a terminal.

2.  Type:

  -------------------------------------------------------------------------
  geth \--testnet \--datadir=. \--syncmode \"fast\" \--cache 1024 console
  -------------------------------------------------------------------------

The **fast syncmode** gets the block headers, the block bodies and does
not process any transactions until current block. The **cache** flag can
be used to change the default megabytes of allocated memory to internal
caching.

![](/assets/exercises-syncing-ropsten-testnet-ethereum-01.png)

Add the Ropsten Peers
---------------------

Now we will **add the peers** which we know run the Ropsten Testnet.

```
+-----------------------------------------------------------------------+
| admin.addPeer("enode://1021f7299d0c4a4559c8f1428e3e7329027c5761ebb    |
| 9d156f0206c74c1b8db73976862c45ad030cfe262fde3686f8ad82186c259067c3bb3 |
| db398e270fd66065@128.199.106.72:30303");                              |
|                                                                       |
| admin.addPeer("enode://2426501653684b8e36c566ed9878bf45cc824a1b37c    |
| 8e208992ef42da08e79c5efee513dc5c85bc3824e694f82a5f4eab168a3d05adc14a7 |
| 4a93addc12880129@149.56.141.248:30303");                              |
|                                                                       |
| admin.addPeer("enode://48fdb244d0d58e58a45b8eac229d8b9e185441287b9    |
| 6f610d757c712a4d73b2e41227913bfc1cfeb5acb7ed15919ac28d3069159e82b1688 |
| 4af54e64ac7536c5@223.194.250.186:30303");                             |
|                                                                       |
| admin.addPeer("enode://eaa139e73415bd6ef0c5f28f698178146dd411b7d13    |
| 79838e50d3ab4b783510db37490856b1c7b95578f3828b3ba07da158b0b7786b1a0bc |
| d205157e589c3378@114.215.185.125:30303");                             |
+-----------------------------------------------------------------------+
```

![](/assets/exercises-syncing-ropsten-testnet-ethereum-02.png)

If you have **problems** syncing the chain, have a look here:

<https://gist.github.com/rfikki/c895641b6405c082f68bcf139cf2f7ae> -- a
weekly updated list of the nodes to help you sync the network.

<https://gitter.im/ethereum/ropsten> -- Ropsten chat room
