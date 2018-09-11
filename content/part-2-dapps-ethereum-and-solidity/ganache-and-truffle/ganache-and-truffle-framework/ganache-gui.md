# Ganache GUI
The GUI version of ganache has the same functionalities with easier to use interface.
![](/assets/ganache-truffle-images/ganache-gui.png)

### Accounts Tab
In this tab you can find 10 automatically generated accounts with their private keys, the mnemonic phrase and the derivation path. 

In the top bar you can find:
- **Current block** - The last block in your chain.
- **Gas price** – The gas price, default is 20000000000 wei.
- **Gas limit** – The gas limit, default is 6721975.
- **Network Id** – The network id, can be used to fork the network.
- **RPC server** – The URL and the port of the provider.
- **Search bar** – For faster searching for transactions and blocks.

### Blocks Tab
In this tab you can find each block that is in the chain with its transactions and the gas that is used for the block. 
![](/assets/ganache-truffle-images/ganache-gui-blocks.png)

When you want to see the transactions in the block, click on the block and it will open a new page with the transactions.

![](/assets/ganache-truffle-images/ganache-gui-block.png)

In the block explorer we have block headers:
- Gas used
- Gas limit
- Mined on
- Block hash

After the block headers you can find a list of transactions. 
In each transaction you can find:
- Transaction hash.
- Created contract address, if the transaction is for deploying contract.

### Settings
In the settings page you can customize ganache for your needs. The settings page is divided in 5 tabs.

### 1.Server
![](/assets/ganache-truffle-images/ganache-server-general.png)

You have several options in this tab.
- **Hostname** – The host that you want to use.
- **Port number** – The port that ganache will use
- **Network Id** – The blockchain network identifier
- **Automine** – This option will mine every transaction that you send immediately. If you disable this option you need to specify a block time.
- **Error on Transaction Failure** – **TODO**

### Accounts & Keys
![](/assets/ganache-truffle-images/ganache-gui-settings-account-and-keys.png)

In this tab we have settings for the accounts being generated.
- **Account Default Balance** – The amount of ethers for each account.
- **Total Accounts to Generate** – The accounts that will be generated on startup.
- **Autogenerate HD Mnemonic** – If it is enabled it will generate new mnemonic phrase every time, otherwise it will use the same mnemonic phrase every time.
- **Mnemonic** – The mnemonic phrase that will be used, if “autogenerate mnemonic” is disabled.
- **Lock accounts** – **TODO**


