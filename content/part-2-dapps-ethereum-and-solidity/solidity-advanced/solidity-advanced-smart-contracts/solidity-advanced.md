# Advanced Solidity and Smart Contract Programming

## Functions, Modifiers, Events, Contract Interactions, Error Handling, Libraries

# Table of Contents
- Functions
- Modifiers
- Events
- Special Variables 
- Units
- Error Handling and Debug
- Killing Contract
![](/assets/solidity-advanced-table-of-contents-01.png)
![](/assets/solidity-advanced-table-of-contents-02.png)
![](/assets/solidity-advanced-table-of-contents-03.png)
![](/assets/solidity-advanced-table-of-contents-04.png)


# Functions in Solidity
- Pure Functions, Fallback, Overloading
![](/assets/solidity-advanced-functions-in-solidity-01.png)


# Messages Sent to Contracts
- contract
- address
- user
- invoke afunction
- Solidity code
- **fn1()**
- **fn2()**
- **fn3()**
![](/assets/solidity-advanced-messages-sent-to-contracts-01.png)


# Pure Functions
- **Pure** functions depend on their parameters only
  - Promise **not to read from or modify**the contract state


# The "Fallback" Function
- **Nameless function**
- Cannot have **arguments** or **return** **value**
- **Executed** on a contract **Call** if the initial function **does not exist**
  - Making a **Call without** any **Data** supplied
  - Executed on receiving **ETH** without any **Data** (Must be **payable**)
- Can **execute** complex operations as long as it has enough **Gas**


# The "Fallback" Function

```cs
contract FallbackContract {
  uint public x;
  function() public { x++; }
}

contract Invoker {
  function callFallback(FallbackContract f) public {
    f.call(0xabcdef01);
    // Results in f.x becoming == 1
  }
}
```

<div class="fragment balloon" style="top:14.01%; left:78.63%; width:44.77%">The **fallback function**is invoked when no other function is matched</div>




# Named Arguments in Function Calls
<div class="fragment balloon" style="top:36.04%; left:96.07%; width:32.34%">You can use the  ** operator </div>
<div class="fragment balloon" style="top:67.16%; left:54.98%; width:41.43%">**Named** arguments</div>


# Constant State Variables
- Constants are like in other languages, assigned only once
- Assigned from an expression constant at **compile time**


# Function Modifiers
<div class="fragment balloon" style="top:61.34%; left:59.93%; width:54.66%">Modifiers **inject functionality**before & after a function call</div>
<div class="fragment balloon" style="top:18.75%; left:92.54%; width:36.14%">Define a **modifier** attacheable to any other function</div>


# Events in Solidity
- Logging That Something Was Happened
![](/assets/solidity-advanced-events-in-solidity-01.png)


# Ethereum Events
- **Events** in EVM **log structured data**about something happened
  - These "logs" are **permanently stored**in the current **transaction**
  - DApp developers can **" watch " for events**through the Web3 API

```cs
contract EventsExample {
  event Sum(address addr, uint a, uint b);
  function sum(uint a, uint b) public returns (uint) {
     emit Sum(msg.sender, a, b); // Invoke the event to log its 						arguments
    return a + b;
  }
}
```



# Events are Stored in the Transaction
- Events are stored in the **transaction** logs in the Ethereum blocks
  - Emitting events costs gas, so be careful
  - Events are visible from the Remix IDE
![](/assets/solidity-advanced-events-are-stored-in-the-transaction-01.png)


# Events are Visible by Anyone
- Events are part of transactions, visible at Etherscan:
![](/assets/solidity-advanced-events-are-visible-by-anyone-01.png)


# Callbacks and Events
<div class="fragment balloon" style="top:20.58%; left:73.15%; width:58.18%">The event can be can be traced from the **Web3 API**by filtering for "**Deposit**" to be called</div>


# Watching for Events from JavaScript
<div class="fragment balloon" style="top:43.22%; left:36.19%; width:34.31%">Watch for **changes**</div>
<div class="fragment balloon" style="top:59.51%; left:85.49%; width:39.67%">The **result** will hold the event arguments</div>


# Time and Ether Units
![](/assets/solidity-advanced-time-and-ether-units-01.png)


# Ether Units
- A **literal number**can take a suffix of:
  - **wei** = 1 / 1 000 000 000 000 000 000 ETH
  - **szabo** = 1 / 1 000 000 ETH
  - **finney** = 1 / 1000 ETH
  - **ether**

```cs
https://etherconverter.online
```



# Time Units
- **Suffixes** like seconds, minutes, … after literal numbers convert between units of time
- **Seconds** are the base unit


# Data Locations
- **EVM** has **three** different **storages**
  - **Storage**, **Memory** and **Stack**
- **State** **variables** are always in **storage**
- **Function** **arguments** are in **memory** by **default**
- **Struct**, **array** or **mapping** type reference **storage** by **default**
- **Value** type (i.e. neither **array**, nor **struct** nor **mapping**) are stored in the **stack**
- **Local** and **function** **parameters** can be changed by the **modifiers** **storage** and **memory**.


# Data Locations
- Objects in the **storage** location are persisted in the blockchain
- Objects in the **memory** location are temporary

```cs
contract PersistentStorage {
  uint[] data; // Persistent data kept in the "storage" location
}
```

<div class="fragment balloon" style="top:35.09%; left:30.29%; width:81.64%">Data location "**storage**" assumed implicitly </div>


# Special Variables in Solidity

```cs
Block and Transaction Properties
```

![](/assets/solidity-advanced-special-variables-in-solidity-01.png)


# Special Variables and Functions
- **Always** exist in the global namespace and are mainly used to provide information about the blockchain
- **Transaction** properties:
  - **msg.data**(bytes): complete calldata
  - **msg.sender** (address): sender of the message (current call)
  - **msg.value**(uint): number of wei sent with the message
  - **tx.gasprice**(uint): gas price of the transaction
  - **tx.origin**(address): transaction sender (first caller in the chain)
  - **gasleft**(uint): remaining gas
- More Special Variables: http://solidity.readthedocs.io/
- **Always** exist in the global namespace and are mainly used to provide information about the blockchain
- **Transaction** properties:
  - **msg.data**(bytes): complete calldata
  - **msg.sender** (address): sender of the message (current call)
  - **msg.value** (uint): number of wei sent with the message
  - **tx.gasprice**(uint): gas price of the transaction
  - **tx.origin** (address): transaction sender (first caller in the chain)
  - **gasleft**(uint): remaining gas
- More Special Variables: http://solidity.readthedocs.io/


# Message Sender vs. Transaction Origin

```cs
contract InvokerInfo {
  address public msgSender;
  address public txOrigin;
  function process() {
    msgSender = msg.sender;
    txOrigin = tx.origin;
  }
}
contract Invoker {
  function invoke(InvokerInfo info) { info.process(); }
} 
```

![](/assets/solidity-advanced-message-sender-vs-transaction-origin-01.png)


# Special Variables and Functions
- **Block** properties
  - **block.coinbase** (address): current block miner’s address
  - **block.number**(uint): current block number
  - **now** (uint): current block timestamp (alias for **block.timestamp**)

```cs
function blockCoinbase() view returns (address) { 
  return block.coinbase; }
function blockNumber() view returns (uint) {
  return block.number; }
function blockTimeStamp() view returns (uint) {
  return block.timestamp; }
```



# Built-in Functions
- **Keccak256(...) returns (bytes32)**
  - Computes the **Ethereum-SHA-3 (Keccak-256)**hash
- **Sha256(...) returns (bytes32)**
  - Computes the **Sha256**hash
- **Ripemd160(...) returns (bytes32)** 
  - Computes the **Ripemd160**hash
- **Ecrecover (bytes32 hash, uint8 v, bytes32 r, bytes32 s)returns (address)**
  - Recover the address associated with the **public key** from **elliptic curve signature** or return **zero** on **error**


# Address Related
- **<address>.balance**returns**(uint256)**
  - Returns the Balance of the Address in Wei
- **<address>.transfer(uint256 amount)**
  - Send given amount of **Wei** to **Address**, **throws** on **failure**, forwards 2300 **gas** stipend, **not** **adjustable**
- **<address>.send(uint256 amount)**returns**(bool)**
  - Send given amount of **Wei** to **Address**, returns **false** on **failure**, forwards 2300 **gas** stipend, **not** **adjustable**
- **<address>.call/ callcode / delegatecall (...)**returns **(bool)**
  - **Issue low-level CALL**, returns **false** on **failure**, **forwards** **all** **available** **gas, adjustable**


# Random Numbers in Solidity
- There is **no secure random generator**in Solidity
  - Miners can manipulate the randomness (if they want to)!
- Some apps use a insecure random, based on the last few blocks
- Some partially predictable randomness can be taken from:
  - **Blockhash()** of the previous block
  - **block.timestamp**, **block.coinbase**, **block.difficulty**, **block.number** of the current block


# Insecure Pseudo-Random – Example

```cs
contract InsecureRandomGenerator {
  bytes32 public randseed;

  function pseudoRandom(uint start, uint end)
      returns (uint) {
    randseed = keccak256(abi.encodePacked(randseed, 	block.timestamp, blockhash(block.number-1), 	block.coinbase, block.difficulty, block.number));
    uint range = end - start + 1;
    uint randVal = start + uint256(randseed) % range;
    return randVal;
  }
}
```



# Error Handling
- **Solidity**uses **state-reverting exceptions**to handle errors
  - Such an exception will **undo all changes**made to the state in the current call (and all its sub-calls) and also **flag an error**to the caller
- **require**(bool condition):
  - throws if the condition is not met – to be used for errors in inputs or external components
- **assert**(bool condition):
  - throws if the condition is not met – to be used for internal errors
  - **Consumes**the entire remaining **Gas**
- **revert**():
  - abort execution and revert state changes 


# Error Handling
- **Assert()** style **exception** are generated in following situations
  - Trying to access **array** **index** that is **outside** or **negative**
  - Accessing **bytesN** index that is **outside** of the **length**
  - **Divide** or **modulo** by **zero** **(e.g. 10 / 0 or 10 % 0)**
  - Converting **value** too **big** or **negative** into **Enum** type
- These **exceptions** will **consume** all of the remaining **Gas**


# Error Custom Message
- **require**(bool condition, “Error Message”):
- **assert**(bool condition):
  - Doesn’t support **Custom** **Messages**
- **revert**(“Error Message”):

```cs
if(msg.value > 5 Ether)
revert("Not enough Ether provided.");
```



# Error Handling
- When**exceptions**happen in a **sub-call**, they “bubble up” (i.e. exceptions are rethrown) automatically
- Exceptions to this rule are “**send**” and the low-level functions ”**call**”, “**delegatecall**” and “**callcode**” – those return **false** in case of an exception instead of “bubbling up”
- The low-level “**call**”, “**delegatecall**” and “**callcode**” will return **success** if the calling account is non-existent, as part of the design of EVM
  - Existence must be checked prior to calling if desired
- **Catching** exceptions is not yet possible


# Check Conditions with Require and Assert
<div class="fragment balloon" style="top:26.20%; left:100.48%; width:25.56%">Only allow even numbers</div>
<div class="fragment balloon" style="top:64.56%; left:73.15%; width:31.57%">Assert the transfer is successful</div>


# Transferring Ethers
![](/assets/solidity-advanced-transferring-ethers-01.png)


# Payable Constructor
- Use payable constructor to send ETH at contract creation

```cs
contract Token1000 {
  mapping(address => uint)
    public balances;
   
  constructor() payable {
    balances[msg.sender] += 1000 * msg.value;
  }
}
```



# Payable Fallback
- Contracts can receive ethers, by **payable fallback**function
  - In this example 1 ETH gives 1000 tokens in the sender's balance
<div class="fragment balloon" style="top:37.43%; left:69.62%; width:46.72%">ETH sent to this contract will be handled by this fallback function</div>
<div class="fragment balloon" style="top:66.17%; left:44.95%; width:26.45%">ETH sender</div>
<div class="fragment balloon" style="top:66.17%; left:99.76%; width:28.04%">Amount sent</div>


# Difference Between Send and Transfer
- **Address** types have two members for sending Wei
  - **<address>.transfer**(uint256 amount) 
    - **send** given amount of Wei to Address, **throws exception on failure**
  - **<address>.send**(uint256 amount) **returns** (bool)
    - **send** given amount of Wei to Address, **returns false on failure**

```cs
msg.sender.transfer(1 ether);
```



# Automatic Bill Payer

```cs
contract BillPayer {
  event MoneyReceived(address sender, uint amount);
  event MoneyPaid(address recipient, uint amount);
  function BillPayer() payable public {
    emit MoneyReceived(msg.sender, msg.value);
  }
  function() payable public {
    emit MoneyReceived(msg.sender, msg.value);
  }
  …
}
```



<!-- # Automatic Bill Payer -->

```cs
contract BillPayer {
  …
  function getBalance() public view returns (uint) {
    return this.balance;
  }
  function payBill(uint amount) public payable {
    // TODO: check the bill sender and amount before the payment!
    msg.sender.transfer(amount);
    emit MoneyPaid(msg.sender, amount);
  }
}
```



# Contract Kill
- **Killing contracts**does not really clean up
  - If Ether is sent to **removed contracts**, the Ether will be **forever lost**
- Contract **disable**
  - Make all functions to throw and **impossible to using**contract
  - All ether sent to the contract will be **returned automatically**

```cs
contract Mortal {
  address private owner;
  function Mortal() { owner = msg.sender; }
  function kill() { 
    require(msg.sender == owner);
    suicide(owner); 
  }
}
```

<div class="fragment balloon" style="top:70.90%; left:63.45%; width:32.51%">**Recover** the funds on the contract </div>
<div class="fragment balloon" style="top:42.29%; left:95.96%; width:40.53%">Executed at **initialization** Assigns the owner</div>


# Contract Kill
- The current contract, explicitly **convertible**to**address**
- **Destroy** the current contract, **sending** its funds to the **given address**
- Alias to **selfdestruct**


# Creating Contracts via "new"
- A contract can create a **new** **contract**
  - Using the **new** keyword
  - The contract is **persisted in the blockchain**at certain address
- The **full code**of the contract being created has to be **known in advance**
  - So **recursive creation-dependencies**are **not possible**
- If the **creation fails**(due to out-of-stack, not enough balance or other problems), **an exception is thrown**




# Creating Contracts via "new"
- **Sending Value on creation with “new”**
<div class="fragment balloon" style="top:32.75%; left:57.33%; width:31.02%">**Amount** you want to send in **Wei**</div>
<div class="fragment balloon" style="top:37.42%; left:92.54%; width:31.02%">Passing the **Arguments**</div>


# External Function Calls
- When calling functions of **other contracts**
  - You can use **.value()**to send money and **.gas()** to limit the gas


# Inheritance

```cs
pragma solidity ^0.4.24;

contract Owned {
  constructor() public { owner = msg.sender; }
  address internal owner;
}

contract Terminatable is Owned {
  function terminate() public {
    require (msg.sender == owner);
    selfdestruct(owner);
  }
}
```

<div class="fragment balloon" style="top:13.75%; left:64.77%; width:29.09%">**Base** contract (parent class)</div>
<div class="fragment balloon" style="top:35.34%; left:91.66%; width:33.50%">**Derived** contract (child class)</div>
<div class="fragment balloon" style="top:62.69%; left:74.03%; width:48.48%">**Destroys** the contract, its stored data and removes it from the blockchain</div>
<div class="fragment balloon" style="top:51.86%; left:93.86%; width:33.50%">**owner**is derived</div>


# Summary
- **Functions** – view, pure, fallback
- Function **overloading**
- Function **modifiers** – private, public, external
- **Events** and **callbacks**
- **Creating** **contracts** via **new**
- **Units** ether units, time units 
- **Globally available variables**, e.g. **block.timestamp**, **tx.origin**
- **Special** variables and functions
![](/assets/solidity-advanced-summary-01.png)



# Resources
- Solidity: https://solidity.readthedocs.io
- OpenZeppelin:  https://github.com/OpenZeppelin/zeppelin-solidity 
- Ethereum Package Management (EthPM): https://www.ethpm.com/, https://github.com/ethpm/ethpm-spec 




