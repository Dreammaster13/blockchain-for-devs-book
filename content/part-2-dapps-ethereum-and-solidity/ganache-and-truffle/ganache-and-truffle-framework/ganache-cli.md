# Ganache CLI

Ganache-cli is a node module that you can use if you prefer command-line interface. Ganache-cli is written in JavaScript and distributed as a Node package via **npm**
```
$ npm install -g ganache-cli
```
After successful installation you will have ganache-cli command in your terminal.
```
$ ganache-cli <options>
```
You have a lot of options you can specify before running your ganache-cli. If you type just **ganache-cli** command it will load the default options. You will receive 10 Ethereum addresses, each one will have 100 ethers. You can use this accounts for deploying contracts and send transactions.

![](/assets/ganache-truffle-images/ganache-initial-accounts.png)

**Disclaimer: Do not use these accounts on production**

You have the corresponding private keys for them.

![](/assets/ganache-truffle-images/ganache-private-keys.png)

These accounts are generated from deterministic wallet and you have the mnemonic phrase for unlocking this wallet.

![](/assets/ganache-truffle-images/ganache-hd-wallet.png)

Additional information that you will have is the Gas Price, Gas Limit and the URL of the RPC (Remote procedure call)

![](/assets/ganache-truffle-images/ganache-gas-settings.png)

These settings can be changed from the options parameters.

### Options
You have several settings that you can specify when running a **ganache-cli**.

- **-a** or **--accounts**: Specify the number of the accounts to generate at startup. Default is 10 
- **-e** or **--defaultBalanceEther**: Amount of ether to assign each test account. Default is 100 ethers.
- **-b** or **--blockTime**: Specify the blockTime in seconds for automatic mining. If you do not specify this flag, ganache will instantly mine a new block for every transaction. Using the –blockTime flag is discouraged unless you have tests which require a specific mining interval.
- **-d** or **--determenistic**: Generate determenistic address based on pre-defined mnemonic phrase
- **-n** or **--secure**: Lock available accounts by default
- **-m** or **--mnemonic**: Use bip39 mnemonic phrase for generating a PRNG seed, which is in turn used for hierarchical deterministic (HD) account generation.
- **-p** or **--port**: Port number to listen on. Default is 8545.
- **-h** or **--host** or --hostname: Hostname to listen on. Defaults to 127.0.0.1 (defaults to 0.0.0.0 for Docker instances of ganache-cli)
- **-s** or **--seed**: Use arbitrary data to generate the HD wallet mnemonic to be used.
- **-g** or **--gasPrice**: The price of gas in wei. Default is 20000000000
- **-l** or **--gasLimit**: The block gas limit. Default is 0x6691b7
- **-f** or **–fork**: Fork from another currently running Ethereum client at given block. Input should be the HTTP location and port of the other client, e.g. http://localhost:8545. You can optionally specify the block to fork from using @ sign: http://localhost:8545@1599200
- **-i** or **–networkId**: Specify the network id ganache-cli will use to identify itself (defaults to the current time or the network id of the forked blockchain it configured)
- **--db**: Specify a path to a directory to save the chain database. If a database already exist, ganache-cli will initialize that chain instead of creating a new one.
- **--debug**: Output VM opcodes for debugging
- **--mem**: Output ganache-cli memory usage statistics. This replaces normal output
- **-v** or **–verbose**: Log all requests and responses to stdout
- **-?** Or **–help**: Display help information
- **--version**: Display the version of ganache-cli
- **--noVMErrorsOnRPCResponse**: Do not transmit transactions failures as RPC errors. Enable this flag for error reporting behavior which is compatible with other clients such as geth and parity
- **--allowUnlimitedContractSize**: Allows unlimited contract sizes while debugging. By enabling this flag, the check within the EVM for contract size limit of 2 KB is bypassed. Enabling this flag will cause ganache-cli to behave differently than production environments. Enabling this flag will cause ganache-cli to behave differently than production environments.



These settings are for advanced usage, if you are running **Ganache** for first time use the default settings.

**Disclaimer: The examples are made with Ganache-cli v6.1.6 (ganache-core: 2.1.5) if you use different version it is possible some difference in the syntax.**










