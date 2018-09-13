# Migrations
Migrations are JavaScript files that help you to deploy contracts. These files are responsible for our deployment tasks and the `Migration.sol` contract keep record of them. 

In the `migrations` folder you can find the tasks for deployment. Truffle automatically makes `1_initial_migration.js` when you initialize project.

When we open the file we will see this code
```js
var Migrations = artifacts.require("./Migrations.sol");

module.exports = function(deployer) {
  deployer.deploy(Migrations);
};
```
In the first line we are getting the compiled smart-contract from the `build` directory.

`var Migrations = artifacts.require("./Migrations.sol")`

After that we are deploying the contract with these lines
```
module.exports = function(deployer) {
  deployer.deploy(Migrations);
};
```
This is just simple deployment script, if we need we can make more complex deployment with link libraries and deploy contract and pass the address in other contract that we will deploy as well.

### Lets Migrate Contract
Let's make it from scratch, first we will write a contract and we will write a migration for it after that we will run it. When we finish with this contract we will make more advanced migration.

```js
pragma solidity ^0.4.24;

contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public constant returns (uint) {
        return storedData;
    }
}
```

 Save the contract in the contracts folder and make new file in migrations folder. We have a name convention for the migrations. We have number **(1,2,3)**, this is the order of execution, **1** - will run first, **2** - will run after that etc. etc. underscore and the name of the script. 
 e.g `2_deply_simple_storage.js`

  ```js
var SimpleStorage = artifacts.require("./SimpleStorage");

module.exports = function(deployer) {
  deployer.deploy(SimpleStorage);
};
```
Now we can **migrate** our contracts. 

```
$ truffle migrate
```
Output
```
using Network 'development'
Deploying SimpleStorage...
... 0xdaa98dc88755201b99e66213a975542116a2b8a373d89c5a6edd40094a05f52f
Saving successful migration to network...
 ... 0x6e5c6f83b928a01e5b283562bb7b3e6b9142896da0f675912d80668728e289d4
Saving artifacts...
```

Our contracts are deployed to the network and we can see the transactions and to find the addresses of the contracts.

### Advanced migration
Now we will make our migration script more complex. We will deploy the script and after that will set value for the `x` variable.
Open `2_deply_simple_storage.js` again and change content of the file.
 
```js
var SimpleStorage = artifacts.require("./SimpleStorage");

module.exports = function(deployer) {
  deployer.deploy(SimpleStorage).then( (instance) => {
  	instance.set(4)
  })
};
```
Now we deployed the contract and after that were called contract method. 


