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





