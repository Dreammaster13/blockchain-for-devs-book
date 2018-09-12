# Compile Contracts
In this chapter we will write and compile contracts. In our folder structure you find `contracts` folder, this is the folder where we can put our contracts. You will find `Migrations.sol` contract which is responsible for the migrations, do not delete it. 

Now we will create our first contract `SimpleStorage.sol`
```js
pragma solidity ^0.4.24;

contract SimpleStorage {
    uint private storedData;
    
    function set(uint x) public {
        storedData = x;
    }
    
    function get() view public returns(uint) {
        return storedData;
    }
}
```

Now we have a contract and we can compile it. The compile command will generate everything needed for deployment in the `build` directory.
```
truffle compile
```
Output
```
Compiling .\contracts\SimpleStorage.sol...
Writing artifacts to .\build\contracts
```
In the build folder you can find `build/contracts/{contract_name}.json`, this file contains the abi and the bytecode of the contract.



