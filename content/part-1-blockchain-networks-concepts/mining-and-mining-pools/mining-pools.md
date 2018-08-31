# Mining Pools

There are basically two options when it comes to cryptocurrency mining:

1. Solo mining.
2. Mining in a pool.

Mining "solo" is the simple, straight-forward solution: you run a network node, collect transactions, try to create a valid block by iterating the nonce. The problem is, you will very rarely find a block if there are lots of other miners, since the probability of finding a block is proportional to your own hash rate divided by the total network hash rate.

In pooled mining, you band together with lots of other miners, and when one of you finds a block, you split the reward with everybody else who contributed. If we disregard the pool fees (which are usually relatively small, typically around 1%), you end up making the same amount over time, but instead of one big payment every couple of years, you get smaller payments every day or every week - in other words, pooled mining decreases the *variance* of your payouts.

## How Do Pools Work?

The above immediately raises some questions - like, how do we split the rewards fairly?

Part of the answer is, Proof-of-Work! Miners connected to a pool get paid for submitting "shares", blocks that might not meet the network's requirements, but meet the pool's requirements. Then, the pool relies on the fact that some of these shares will "overshoot", and be of such high quality that they will be accepted even by the network itself; when that happens, the pool has found a block.

When it comes to splitting the rewards themselves, there are many methods:

* Proportional
* Pay-per-Share (PPS)
* Pay-per-Last-N-Shares (PPLNS)
* Geometric method

...and others. The more advanced splitting methods exist to prevent "pool hopping", an issue that arises with pools that use the proportional method (if a certain round has seen many shares, a share will end up being worth less than normal, so miners are incentivized to temporarily abandon the pool and "hop" on another one).

In our experience, PPLNS is pretty common.

## The Problem with Pools

In practice, most people end up joining pools - practically everybody except the largest mining farms. This places a lot of power in the hands of pool operators, since they are the ones putting together the blocks. Here's how the pool statistics might look like for Bitcoin:

![](/content/part-1-blockchain-networks-concepts/mining-and-mining-pools/bitcoin-pools.png)

(*Source: https://www.blockchain.com/pools*)

...and here's Ethereum:

![](/content/part-1-blockchain-networks-concepts/mining-and-mining-pools/ethereum-pools.png)

(*Source: https://etherscan.io/stat/miner*)

Notice that just a couple of these pools banding together might result in them having enough hash power to perform a [51% attack](https://en.bitcoin.it/wiki/Majority_attack).

There have been attempts to fix that at the pool protocol level, by letting individual miners create blocks themselves, and merely submit proofs to the pool that they have included them as receiver of the coinbase transaction (because obviously the pool wouldn't want to pay for shares that don't have them as reward receiver). But it seems the main thing stopping pools from performing such attacks are actually game-theoretic considerations.