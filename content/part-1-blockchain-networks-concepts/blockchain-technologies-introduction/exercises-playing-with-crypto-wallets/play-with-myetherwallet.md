# Exercises: Playing with Blockchain and MyEtherWallet

In this exercise we shall install a **cryptocurrency wallet** and will play with **cryptocurrencies**. We shall install wallet software, generate **private keys** and digital currency **addresses** , send **transactions** , track the transaction processing.

For this exercise we shall use Web-based crypto-wallet software called **MyEtherWallet** (**MEW**), which behaves like locally installed Ethereum crypto wallets, but is accessible through the Web, without any software installation.

- MyEtherWallet is a **client-side wallet software**. It does not store your private keys, neither sends them at the server-side. Keeping your private keys is a secure place is your obligation.
- MEW connects to the Ethereum blockchain through **JSON RPC API** over HTTP (using client-side AJAX calls from JavaScript). The MyEtherWallet API is officially documented here: [https://www.myetherapi.com](https://www.myetherapi.com).
- You can create / export / import **wallet keys** , sign and **send transactions** and **browse the blockchain**.
- MEW works with the **main** (production) Ethereum network ( **mainnet** ), as well as with testing networks ( **testnets** ) like Ropsten, Kovan and Rinkeby.

1. 1.Create a Crypto Wallet

First, we shall generate an Ethereum wallet using the online wallet app called &quot; **MyEtherWallet**&quot;.

1. Open [https://www.myetherwallet.com](https://www.myetherwallet.com/) in your Web browser. It should look like this:

 ![](/assets/exercises-playing-with-crypto-wallets-01.png)
1. Now look at upper right corner and choose to connect to one of the **test networks** there. The default is the main net which uses real ethers. We want to use test net ethers, so choose the **&quot;Ropsten&quot; testnet**.

 ![](/assets/exercises-playing-with-crypto-wallets-02.png)
1. **Create a New Wallet**. First you should write password and then create the wallet.

 ![](/assets/exercises-playing-with-crypto-wallets-03.png)
This will generate **a random private key** in your Web browser along with its corresponding Ethereum address. Your private key may be stored in an **encrypted keystore file** (recommended) or can be kept in **pure unencrypted** format (not recommended, unless when you print it on a paper).

1. Download the **encrypted**** UTC ****JSON keystore file** , then continue.

- The **JSON keystore file** holds your 256-bit private key, strongly **encrypted** by your **password** (using **SCrypt** for password-based key derivation function + **AES** as an encryption algorithm).
- The format of the UTC JSON keystore file is described here: [https://goo.gl/G6TbLf](https://goo.gl/G6TbLf).
- If you lose the keystore file, you cannot restore your private key. It will be permanently lost.
- If you forget your password, you cannot restore it. You may try to crack it by a password cracker (like [https://github.com/burjorjee/pyethrecover](https://github.com/burjorjee/pyethrecover)), but generally the chances to succeed are not good.

 ![](/assets/exercises-playing-with-crypto-wallets-04.png)
1. Optionally save your **private key** (unencrypted). Do not show it to anyone! Your private key is also stored in the encrypted JSON keystore file, so you may skip saving it unencrypted.

 ![](/assets/exercises-playing-with-crypto-wallets-05.png)
1. Now **unlock your wallet** using your JSON keystore file (decrypt it, using your keystore password).

 ![](/assets/exercises-playing-with-crypto-wallets-06.png)
1. You can see your **Ethereum Account Address** (derived from your public key), **Token Balances** , **Account Balance** and **Private Key** there:

 ![](/assets/exercises-playing-with-crypto-wallets-07.png)
1. 2.Get an Initial Amount of Ethers

Now you have a wallet, but it is **empty** , i.e. balance == 0 ETHt ( **ETHt** == Ethereum test ethers). Let&#39;s **get some ethers** to be able to play with transactions and payments. Typically, the **testnets provide coins for free** , after some kind or registration or request.

We are using the **Ropsten test network**. We can request ETHt through some **Ropsten faucet** like:

- [http://faucet.ropsten.be:3001](http://faucet.ropsten.be:3001)
- [https://faucet.bitfwd.xyz](https://faucet.bitfwd.xyz)

### Ropsten.be Faucet

You may request 1 ETHt from the **Ropsten official testnet faucet** : [http://faucet.ropsten.be:3001](http://faucet.ropsten.be:3001).

 ![](/assets/exercises-playing-with-crypto-wallets-08.png)
### bitfwd&#39;s Ethereum Ropsten Faucet

You may request 1 ETHt from the **bitfwd&#39;s Ethereum Ropsten Faucet** : [https://faucet.bitfwd.xyz](https://faucet.bitfwd.xyz).

 ![](/assets/exercises-playing-with-crypto-wallets-09.png)
 ![](/assets/exercises-playing-with-crypto-wallets-10.png)
1. After the transactions are processed by the blockchain you should have ethers in your account. Go to **&quot;View Wallet Info&quot;** and unlock your wallet. Congrats, now you have ethers and you can operate with them!

 ![](/assets/exercises-playing-with-crypto-wallets-11.png)
1. 3.Send Ethers to Another Address

After creating an Ethereum testnet account and receiving some ethers now you can send ethers to someone else.

1. Get someone&#39;s address from the class and send him/her some ether, e.g. 0.5 ROPSTEN ETH (ETHt).
2. Unlock your account with the **JSON file** and go to the **&quot;Send Ethers &amp; Tokens&quot;** tab. Put the **address** of your mate and the **amount** you want to send. The **Gas Limit** is the default one. Generate the transaction. Then click **Send Transaction.**

 ![](/assets/exercises-playing-with-crypto-wallets-12.png)
1. You will see the following window and you should click **&quot;Yes, I am sure! Make transaction&quot;** :

 ![](/assets/exercises-playing-with-crypto-wallets-13.png)
1. Now click &quot;Verify Transaction&quot;

 ![](/assets/exercises-playing-with-crypto-wallets-14.png)
 ![](/assets/exercises-playing-with-crypto-wallets-15.png)
1. Now you should have smaller amount of ethers (you&#39;ve send 0.5 but there is also a transaction fee):

 ![](/assets/exercises-playing-with-crypto-wallets-16.png)
You can also see this info in MyEtherWallet.

# 2.What to Submit?

Submit as exercise outcome the **URL of your Ethereum address** in the Ropsten network at EtherScan, e.g.:

- [https://ropsten.etherscan.io/address/0xb97e993872a903850c07fbd999a6e750963ef195](https://ropsten.etherscan.io/address/0xb97e993872a903850c07fbd999a6e750963ef195)

You should some **ETHt** in your balance, as well as some transaction history of ETHt transfers.

Examples:

 ![](/assets/exercises-playing-with-crypto-wallets-17.png)