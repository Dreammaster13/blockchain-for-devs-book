# Truffle Install and Configure
Truffle is built with JavaScript and you can easy install it with the **npm** package manager.

```
$ npm install -g truffle
```
After that you will have **truffle** command available in your terminal. To initialize new truffle project you can use **truffle init** command.
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
