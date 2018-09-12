# Truffle Install and Configure
Truffle is built with JavaScript and we can easy install it with the **npm** package manager.

```
$ npm install -g truffle
```
After that we will have **truffle** command available in our terminal. To initialize new truffle project we use **truffle init** command.
```
$ mkdir myProject
$ cd myProject
$ truffle init
```
Output
```
Downloading...
Unpacking...
Setting up...
Unbox successfull. Sweet!

Commands:
   Compile:        truffle compile
   Migrate:        truffle migrate
   Test contracts: truffle test
```

Truffle generated for us basic project with contracts, migrations and tests. The project structure that we have now is: 
```
contracts
migrations
test
truffle.js
truffle-config.js
```
## Configure networks
We have 2 files for our configuration `truffle.js` and `truffle-config.js`. The both files can be used for configuration. If you are using Windows when you use `truffle` command you will receive script error, because windows tries to run the file. You can use **Powershell** or delete `truffle.js` file and use only `truffle-config.js`. In the examples in this chapter we will use **powershell** instead cmd.

In the `truffle.js` file we must specify the network, this network will be used for migrating and deploying contracts to this network. If you developing and you want to test your contracts, use **ganache**, because the transactions will be executed immediately and you will save time.

```js
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 8545,
      network_id: "*" // Match any network id
    }
  }
};
```
Now you can run `truffle migrate` and you will migrate your contracts, now have one that comes with truffle. If everything is alright you will receive `Network up to date`, otherwise you will receive `Error: No network specified. Cannot determine current network.`

You can specify more than one network, which is very helpful because you can easy deploy to **Mainnet** or other network.

```js
networks: {
  development: {
    host: "127.0.0.1",
    port: 8545,
    network_id: "*" // match any network
  },
  live: {
    host: "178.25.19.88", // Random IP for example purposes (do not use)
    port: 80,
    network_id: 1,        // Ethereum public network
    // optional config values:
    // gas
    // gasPrice
    // from - default address to use for any transaction Truffle makes during migrations
    // provider - web3 provider instance Truffle should use to talk to the Ethereum network.
    //          - function that returns a web3 provider instance (see below.)
    //          - if specified, host and port are ignored.
  }
}
```
Now we have two networks, we can specify **gas limit** and **gas price** and truffle will use it when make transactions.

When you finish with the development you can migrate your contracts directly in the Mainnet.
```
$ truffle migrate --network live
``` 
After this command your contracts will be deployed to the Mainnet.






