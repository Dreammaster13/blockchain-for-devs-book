# What is Mining?

As we covered in the previous chapter ([Consensus Algorithms](/content/part-1-blockchain-networks-concepts/consensus-algorithms/overview.md)), mining is one possible way to protect the network against [Sybil attacks](https://en.wikipedia.org/wiki/Sybil_attack), by letting the network participants "vote" in proportion to their computational power, thus making it expensive to gain network majority by creating fake accounts.

If you're wondering why it's called "mining", it's because it's also the process by which new coins are created and put in circulation - so in this way it's similar to e.g. mining gold, except here we're "mining" virtual coins.

# How Does It Work?

Mining is basically a "computational lottery", where the goal is to find a partial collision in a hash function (or other one-way function). If the hash function is not broken[^1], it's not possible to predict how you need to change a certain piece of data to make its hash come out in a certain shape (e.g. starting with $$n$$ zero bits, where $$n$$ is some number that can be dynamically adjusted by the network) - thus you have no choice but to try different values, as fast as you can, until you find the "winning ticket"!

To make this a bit more concrete, let's take Bitcoin for example. Miners there do the following:

1. Collect transactions from the network and build a block.
2. Pick a starting nonce.[^2]
3. Iterate until ```SHA256(SHA256(block_header))``` meets the network difficulty requirements.[^3]
    
The network difficulty changes over time, so that new blocks are created roughly every 10 minutes, no matter how many miners are there - if more miners join, the difficulty increases; if they leave, it decreases.

When a miner is successful at finding the proper nonce, they broadcast the block to the network, and other nodes will validate it and eventually add it to their chains.

To see a visualization of the mining process in your browser, try [http://yogh.io/#mine:last](http://yogh.io/#mine:last)

![](/content/part-1-blockchain-networks-concepts/mining-and-mining-pools/live_miner.png)

[^1]: A hash function is "cryptographically broken" when it fails to meet one of the criteria for cryptographic hash functions outlined in the previous chapter on [hash functions](/content/part-1-blockchain-networks-concepts/blockchain-cryptography/blockchain-cryptography-overview/hash-functions.md).
[^2]: A nonce in this context is a field in the header that doesn't matter, except when it comes to making the hash come out different.
[^3]: Hashing twice is needed in SHA-2 to protect it against [length extension attacks](https://en.wikipedia.org/wiki/Length_extension_attack).