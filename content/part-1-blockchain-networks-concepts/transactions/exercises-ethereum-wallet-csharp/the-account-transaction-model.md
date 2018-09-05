# The Account Transaction Model

In contrast, Ethereum uses the more intuitive, but harder to implement efficiently and a bit less secure **account model** - where every address is an account that has a balance, just like accounts in a bank.

Sending money is a matter of subtracting from the balance of one account and adding to another. Graphically, this looks like this:

![](/content/part-1-blockchain-networks-concepts/transactions/blockchain-transactions/acct.png)

In this model, the wallet just holds the private keys to all of the accounts (addresses) that you control, and the total balance is just the sum of their individual balances.

If you're wondering why they didn't go with the UTXO model, the reasons will become clear in the second part of the book, where we talk in detail about smart contracts.