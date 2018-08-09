# Mining Rewards

Miners get rewarded for helping secure the network in two ways:

1. Block subsidy.
2. Transaction fees.

The block subsidy is a special transaction (called "coinbase[^1] transaction") that miners get to add once per block, with a pre-determined output amount. This is the only transaction that is allowed to not reference any inputs - it essentially creates new coins. In Bitcoin the subsidy started out at 50 BTC, and is halved every 210,000 blocks; at the time of writing this book, it's 12.5 BTC. It will go down to zero in the year 2140.

The transaction fees are the difference between the sum of the inputs and the sum of the outputs - users determine what fees they want to pay by not using up the entire inputs, and miners determine what transactions they'll include in a block based on how much they will profit. Usually miners are looking at "Satoshis[^2] per byte", because there's a limit to how big blocks can be, so accepting a large transaction might mean not having room for several smaller ones.

# Mining difficulty

In order to keep the block time relatively constant (e.g. 10 minutes in Bitcoin), even when the total hash rate of the miners in the network fluctuates, the requirements for which block hashes are considered "acceptable" can change dynamically. In Bitcoin, every 2016 blocks the timestamps of the blocks are evaluated, and if they're less than 10 minutes apart (on average), the difficulty will increase; the hashes will be required to have a smaller numeric value than what was required before. Conversely, if they are more than 10 minutes apart, the difficulty will be decreased - the "limit" will be moved up, so that more possible hashes are acceptable. Here's a graph of Bitcoin's mining difficulty over time:

![](/content/part-1-blockchain-networks-concepts/mining-and-mining-pools/difficulty.png)

Something interesting to note is that there's a correlation between Bitcoin's price and mining difficulty; as Bitcoin increases in value, more miners are attracted to it, thus increasing its security (a network with more hash rate is harder to attack).

In the next chapter, we will talk about [mining pools](/content/part-1-blockchain-networks-concepts/mining-and-mining-pools/mining-pools.md).

[^1]: Not related to the cryptocurrency exchange of the same name.
[^2]: A Satoshi is the smallest unit of Bitcoin, kind of like cents for US dollars.