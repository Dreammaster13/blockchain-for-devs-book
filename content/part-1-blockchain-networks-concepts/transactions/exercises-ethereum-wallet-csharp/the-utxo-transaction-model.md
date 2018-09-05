# The UTXO Transaction Model

Bitcoin and other cryptocurrencies are based on something called UTXOs - Unspent Transaction Outputs.

The idea is, each transaction must reference as **inputs** some other transaction's unspent transaction **outputs**. Then, the outputs of this transaction become UTXOs that the recipient can spend by using them as inputs to another transaction. Graphically, the "flow" of money looks like this:

![](/content/part-1-blockchain-networks-concepts/transactions/blockchain-transactions/utxo.png)

So, when your wallet is telling you how much Bitcoin you have, it's actually not as simple as looking up a number - instead, it must find all UTXOs that are locked in a way that would allow you to spend them, then sum their values.

As an analogy, you can think of an UTXO as a **bank note** in your wallet. The main difference being they don't come in fixed amounts, but the amount is determined by the sender.

The above may sound a bit complicated, but it has a big advantage when it comes to how easy it is to implement **efficiently**. For example, everything that a node needs to know in order to validate a new transaction is the **UTXO set**, which is relatively constant in size:

![](/content/part-1-blockchain-networks-concepts/transactions/utxo_set.png)

*(from https://statoshi.info/dashboard/db/unspent-transaction-output-set)*

Note this set is much smaller than the blockchain itself, since once a transaction has no more unspent outputs, it can be dropped. In fact, the UTXO set is small enough to fit completely in RAM on an average computer (while the entire Bitcoin blockchain, at the time of writing this book, is around 180GB in size).