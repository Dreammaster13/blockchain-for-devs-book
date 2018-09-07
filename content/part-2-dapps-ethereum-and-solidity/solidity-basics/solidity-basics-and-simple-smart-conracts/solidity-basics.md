# Solidity Basics: Writing Simple Smart Contracts

## Language Overview, Writing Solidity Code

# Table of Contents
- What is **Solidity**?
- Ethereum Virtual Machine (**EVM**)
- Solidity Dev Environment & **IDEs**
  - Compile, Publish, and Test Contracts
- **Smart Contract**Basics
- Solidity Language Basics
  - Contracts, functions, data types, arrays,maps, structs
![](/assets/smart-contracts-and-solidity-basics-table-of-contents-01.png)
![](/assets/smart-contracts-and-solidity-basics-table-of-contents-02.png)
![](/assets/smart-contracts-and-solidity-basics-table-of-contents-03.png)


# Ethereum Virtual Machine and Solidity
- Architectural Concepts
![](/assets/smart-contracts-and-solidity-basics-ethereum-virtual-machine-and-solidity-01.png)


# What is Solidity?
- **Solidity** is a contract-oriented, high-level **programming language**
  - Syntax similar to JavaScript and C#
  - Runs in the **Ethereum Virtual Machine**(EVM)
  - Statically typed language (like C# and Java)
  - Complex user-defined types (structs)
  - Contracts and inheritance (like in OOP)
  - Libraries (like in any other dev platform)
- Official documentation: https://solidity.readthedocs.io
![](/assets/smart-contracts-and-solidity-basics-what-is-solidity-01.png)


# Solidity Code Compilation
- **Ethereum Virtual Machine**(EVM) is the environment where the contracts are executed
  - Code execution costs money (called **gas**)
- **Application Binary Interface**(ABI) – describes the contract’s interface
  - Public **methods** + **input** arguments + **return values**+ contract **events**
- Solc compiler
- Solidity Code
- Bytecode (EVM instructions)
- ABI definition


<!-- # Solidity Code Compilation -->
- To publish the contract, the **bytecode**is uploaded to the blockchain
- To **access** it, you need the **ABI definition**to know what inputs and outputs the contract operates with
- Demo in Remix
- Ethereum Blockchain
- Accessing the contract
- Bytecode (EVM instructions)
- ABI definition


# Transaction Validation in EVM
- **EVM** uses validators to ensure transactions are OK
  - **Validators** take a transaction and apply it executing the associated code, make sure that:
  - The **transaction** is **valid** (e.g. encoding, sender signature, constraints, etc.)
  - The **sender** has enough funds to **pay** for the execution
  - The **EVM** did not throw any exceptions during the execution


# Ethereum Gas Measurement
- Contracts **aren’t free**, execution costs **gas**
- **Gas**is the internal unit for keeping track of execution cost
- **Gas** measures the consumed computational resources
  - Each CPU instruction in EVM costs gas: **1 gas = 1 computational step**
  - Each persistent storage write also costs gas
- E.g. writing 32 bytes in the contract memory costs 80 000 gas
- **Gas price** can be negotiated (cannot be 0 to avoid spam):
  - **1 gas ~= 20 Gwei (dynamic)**


# Gas Payments
- **Gas** is measured and paid for at **each contract execution**
  - Every **transaction** to a contract or contract creation
- **Reading** data from a contract (reading its state) is **free!**
  - Code execution / data storage is paid
- The **gas price** is set by the caller (you)
  - The lower the price, **the more time**it will take for a miner to include the tx in a block
- Best gas price calculator: https://ethgasstation.info


# Gas Limit
- **Gas limit**== **maximum allowed gas usage**in a transaction
  - **Sum of all gas spending**for all operations and storage
- **Do not reach the limit!**
  - Current contract execution will be terminated
  - Any changes to the contract’s state will be reverted


# Operations and Gas
- **Operations that cost gas:**
- Anything that **changes the blockchain state**:
  - **Writing** to contract’s memory
  - **Execution** of contract logic
  - **Uploading** data to blockchain (contract publishing)
- **Free operations:**
- Anything **not requiring changes**, like:
  - **Reading** blockchain data (contracts, their state, …)
- Examples: get contract metadata, check account balance, etc. 


# Solidity in Practice

```cs
Write and Run Solidity Code in Remix IDE
```

![](/assets/smart-contracts-and-solidity-basics-solidity-in-practice-01.png)


# Installing Solidity Dev Environment
- **Remix**
  - In-browser Solidity IDE
  - https://remix.ethereum.org
- Solidity compiler
  - https://www.npmjs.com/package/solc
- Ethereum **ganache-cli**(former **testrpc**) + **Truffle Framework**
  - https://github.com/ethereumjs/testrpc
  - http://truffleframework.com 
![](/assets/smart-contracts-and-solidity-basics-installing-solidity-dev-environment-01.png)


# Playing with Ethereum Remix
![](/assets/smart-contracts-and-solidity-basics-playing-with-ethereum-remix-01.png)


# Contracts Programming Basics
- **Contracts** in Solidity are
  - Like classes and interfaces in the OOP languages
- Contracts may hold
  - **Data** + **functions**
  - Just like classes in OOP
- Contract execution is paid with **gas** consumption
![](/assets/smart-contracts-and-solidity-basics-contracts-programming-basics-01.png)


# Functions in Solidity
- **Functions** are the executable units of code within a contract
- Once defined, can be **invoked** later (with some arguments):


# Example: Simple Storage Contract
<div class="fragment balloon" style="top:20.00%; left:81.63%; width:42.38%">Persistent **data** stored in the blockchain</div>
<div class="fragment balloon" style="top:38.20%; left:87.25%; width:47.05%">Public **member function**: anyone can invoke it</div>
<div class="fragment balloon" style="top:62.34%; left:65.77%; width:51.46%">View **function**: does not change the contract's state</div>


# Compiling the Contract in Remix
![](/assets/smart-contracts-and-solidity-basics-compiling-the-contract-in-remix-01.png)


# Deploying the Contract in a Testing EVM
![](/assets/smart-contracts-and-solidity-basics-deploying-the-contract-in-a-testing-evm-01.png)


# Invoking Functions on the Deployed Contract
![](/assets/smart-contracts-and-solidity-basics-invoking-functions-on-the-deployed-contract-01.png)


# Debugging in Remix
![](/assets/smart-contracts-and-solidity-basics-debugging-in-remix-01.png)


# Debugging in Remix
- The **debugger** allows one to see detailed **information** about the **transaction’s** **execution**
- You can start a **debug** session by providing either a **transaction hash** or a **block number** and **transaction index**
- The **transaction** panel displays basic **information**
- The **navigation** part contains a **slider** and **buttons**
- Low level panels
  - Instructions, Solidity Locals, Solidity State, Stack, Storage Changes,
  -    Memory, Call Data, Call Stack, Return Value.


# Problem: Incrementor Contract
- Write a Solidity contract
  - Contract holds a certain **value**
    - **value** (**uint**)
  - Anyone can **read** the value
    - **get()** &rarr; **uint**
  - Anyone can increment the value
    - **increment(uint delta)**
- value
![](/assets/smart-contracts-and-solidity-basics-problem-incrementor-contract-01.png)


# Solution: Incrementor Contract

```cs
pragma solidity ^0.4.24;
contract Incrementor {
  uint private value;
  function increment(uint delta) public {
    value += delta;
  }
  function get() view public returns (uint) {
    return value;
  }
}
```

<div class="fragment balloon" style="top:20.12%; left:69.95%; width:42.38%">Persistent **data** stored in the blockchain</div>
<div class="fragment balloon" style="top:45.26%; left:58.93%; width:58.18%">Change the persistent data field</div>
<div class="fragment balloon" style="top:63.62%; left:54.47%; width:58.18%">Read the persistent data field</div>


# Function Visibility: Public and External
- **Public** (default)
  - Part of the contract interface, can be **called by anyone**
  - For public state variables, an **automatic getter**function is generated
- **External**
  - Functions designed to be called externally
    - From **other contracts**and by **external transactions**
  - An external function **cannot be called internally**
    - I.e. **f()** does not work, but this**.f()** works
  - Cheaper to execute compared to **Public**

```cs
uint256 public totalSupply;
```



# Function Visibility: Internal and Private
- **Internal**
  - **Accessed** **internally**(i.e. from within the current contract or contracts deriving from it), without using **“ this ”**
  - Like "**protected**" in object-oriented languages
- **Private**
  - Accessible in the contract only
  - Not accessible in the derived contracts

```cs
uint256 internal totalSupply;
```



# Functions in Solidity
- Functions with no output
- Functions returning values

```cs
function increment(uint delta) public {
  value += delta;
}
```

<div class="fragment balloon" style="top:36.02%; left:81.08%; width:53.77%">Function visibility: **external** / **public** / **internal** / **private**</div>
<div class="fragment balloon" style="top:64.64%; left:51.99%; width:43.20%">Promise not to modify the state of blockchain</div>
<div class="fragment balloon" style="top:64.64%; left:102.73%; width:33.00%">Specify explicitly the return type</div>
![](/assets/smart-contracts-and-solidity-basics-functions-in-solidity-01.png)


# Data Types in Solidity
- Data types are similar to most programming languages:
  - **int8** / **uint8**, … **uint256** (**uint**) – integers of 8 … 256 bits
    - No floating-points numbers 
  - **bool** – **true** / **false** value
  - **string** – UTF8-encoded text, e.g. "Hello, Solidity!" or "“
  - **bytes / bytes8 ,**… **bytes32** – Storing information as **bytes** 
  - **address** – Ethereum address (EIP 55 encoded)
    - e.g. 0xdCad3a6d3569DF655070DEd06cb7A1b2Ccd1D3AF
  - **enum** – enumerated type


# Data Types in Solidity
- **int8,int32** …  **int256**/ **uint8**, … **uint256** (**uint**)
- Number **literal** **expressions** retain **arbitrary** **precision** until they are converted to a **non-literal**type 
- Expressions with variables **don’t retain** arbitrary **precision**!
- Integer literal **division** evaluates to a **rational** number

```cs
uint public c = ( 2 / 5 + 1) * 10;
// (0.4 + 1) * 10 = 1.4*10 = 14
```


```cs
uint public a = 0xA3F; // is 2623
```



# Data Types in Solidity
- **Strings**
  - Arbitrary-length **UTF-8 data**
  - Support escape characters -**\n**,**\xNN**and**\uNNNN**
    - **\xNN** takes a **Hex** value and inserts the appropriate **byte**
    - **\uNNNN** takes **Unicode** and inserts the appropriate **UTF-8** sequence
  - No index access. You need to cast it to **bytes**!
  - **Strings** in Solidity are expensive


# Data Types in Solidity
- **Bytes, bytes1, bytes2, … bytes32**
  - Arbitrary-length **raw byte date**
  - Has **default value** of 0 when initialized
  - **bytesX** == new **byte[X]**; 
  - **bytesX [n]** will return the **N- th** **byte**
    - This is Read-only
    - Value is between 0 and 255
  - Better to use **bytesX** instead of **String**


# Data Types in Solidity
- **Address**
- The **address** type is a 20 **byte** value that does not allow any arithmetic operations
- Has **members**
  - **balance** - query the balance of an address
  - **transfer** - can be used for sending Ether other addresses
  - **send** - the lower level counterpart of the member **transfer**
  - **call**, **callcode**, **delegatecall** - discuss in the Advanced lectures


# Data Types in Solidity
- **Enum**
  - **Enums** are one way to create a user-defined type in **Solidity**
  - **Value** ranges checked at runtime
    - Failure causes an **exception**
- **Type Deduction**

```cs
enum Answer {Yes, No, Maybe}
Answer decision = Answer.Yes;
```



# Data Types in Solidity
- [Demo]()
![](/assets/smart-contracts-and-solidity-basics-data-types-in-solidity-01.png)


# Problem: Last Invoker
- Write a Solidity contract
  - Keep the address of its **previous invoker**
  - **getLastInvoker()** &rarr; returns **(bool,** **address)**
    - **true** / **false** – if a previous invoker exists or not
    - The **address** that has invoked the contract before you
![](/assets/smart-contracts-and-solidity-basics-problem-last-invoker-01.png)


# Solution: Last Invoker

```cs
pragma solidity ^0.4.24;

contract LastInvoker {
  address private lastInvoker;

  function getLastInvoker() public
      returns (bool, address) {
    address result = lastInvoker;
    lastInvoker = msg.sender;
    return (result != 0x0, result);
  }
}
```

<div class="fragment balloon" style="top:55.20%; left:93.42%; width:41.71%">The address of the contract's **invoker** is sent as **msg.sender**</div>
<div class="fragment balloon" style="top:16.41%; left:85.49%; width:46.12%">Keep the last invoking address in the contract's persistent storage</div>


# Arrays
- Types of **Arrays** in Solidity
  - **Compile-time** fixed size
  - **Dynamic**
- Can hold arbitrary **types**
  - **Arrays**, **Mappings** or **Structs**
  - **Multidimensional** **Arrays**
- **Array** Members
  - **Length** – returns the number of elements in the **Array**
  - **Push** – appends new elements to **Dynamic Array** 

```cs
bool[2][] pairsOfFlags;
pairsOfFlags[index][0] = true;
pairsOfFlags[index][1] = false;

```



# Arrays

```cs
// Array of fixed size
uint8[3] nums = [10, 20, 30];
nums[0] = 10;
```



# Problem: Array of Facts
- Create a Solidity contract
  - Contract owner (creator) can
    - Add **facts** (string values)
  - Anyone can read the facts
    - **count()** – returns the count of facts
    - **getFact(index)** – returns specified fact by index [0…count-1]
    - Solidity cannot return all facts (array of strings)
  - Nobody can delete facts or destroy the contract
![](/assets/smart-contracts-and-solidity-basics-problem-array-of-facts-01.png)


# Solution: Array of Facts

```cs
contract Facts {
  string[] private facts;
  address private contractOwner = msg.sender;
  function add(string newFact) public {
    require(msg.sender == contractOwner);
    facts.push(newFact);
  }
  function count() view public returns (uint) {
    return facts.length;
  }
  function getFact(uint index) view public returns (string) {
    return facts[index];
  }
}
```

<div class="fragment balloon" style="top:6.68%; left:64.77%; width:46.28%">Hold all the facts in **array** stored on the blockchain</div>
<div class="fragment balloon" style="top:38.47%; left:61.69%; width:60.83%">Append an element into the array</div>
<div class="fragment balloon" style="top:68.65%; left:62.57%; width:65.23%">Solidity functions cannot return **string[]** so we use a workaround</div>
<div class="fragment balloon" style="top:22.74%; left:96.07%; width:22.04%">Check for ownership</div>


# Maps
- Key-value Pair – **mapping(_keyType => _valueType)**
  - **_keyType**– Any type except for a **mapping**, a dynamically sized **array**, a **contract**, an **enum** and a **struct**
  - **_valueType**– can actually be **any** type, including **mappings**.
- **The key is not stored**, its **keccak256** is used to look up the value
  - Impossible to retrieve the **keys**
  - Impossible to retrieve the values **without** the **keys**
- **Values** are **initialized** with the **default** **value** of their **type**


# Maps

```cs
struct Account {
  string personName;
  uint amount;
}
mapping (address => Account) accByAddr;
accByAddr[0xdCad3a6d3569DF655070DEd06cb7A1b2Ccd1D3AF] =
 Account("Peter", 120);
```

<div class="fragment balloon" style="top:38.36%; left:58.86%; width:51.31%">Mappings can be used as **fields** in the contracts only. No instantiation is needed.</div>


# Structs
- **Structs** are a composition of more primitive types
  - Doesn’t support **Struct** **Methods**
  - Doesn’t support **Modifiers**
  - **No inheritance, polymorphism and encapsulation**
- **Not possible**to contain, a member of its **own type**
- You can store **Structs** inside **Mappings** and **Arrays**
- **Direct** **access** to the members of **Struct**


# Structs
<div class="fragment balloon" style="top:27.86%; left:71.39%; width:35.24%">Creating an **object** of given structure</div>
<div class="fragment balloon" style="top:71.47%; left:55.29%; width:64.35%">Accessing a **field** from the structure</div>
<div class="fragment balloon" style="top:52.06%; left:76.85%; width:45.89%">Creating another **object**</div>
<div class="fragment balloon" style="top:4.68%; left:55.24%; width:43.20%">A simple **structure** holding two data fields</div>


# Problem: Registry of Certificates
- A company issues **certificates** for completed trainings
  - Each certificate has its data and content calculated as **hash**
  - The registry of all valid certificate hashes stored on the blockchain
  - Owner can add certificate hashes: **add(hash)**
  - Anyone can verify а certificate by its hash: **verify(hash)**
![](/assets/smart-contracts-and-solidity-basics-problem-registry-of-certificates-01.png)
![](/assets/smart-contracts-and-solidity-basics-problem-registry-of-certificates-02.png)


# Solution: Registry of Certificates

```cs
contract Certificates {
  mapping (string => bool) private certificateHashes;
  address contractOwner = msg.sender;

  function add(string hash) public {
    require (msg.sender == contractOwner);
    certificateHashes[hash] = true;
  }

  function verify(string hash) view public
      returns (bool) {
    return certificateHashes[hash];
  }
}
```

<div class="fragment balloon" style="top:27.60%; left:93.57%; width:41.84%">Contract owner only</div>
<div class="fragment balloon" style="top:41.44%; left:92.21%; width:43.20%">Store the certificate hash on the blockchain</div>


# Problem: Create a Simple Token
- Create a **simple token**contract
  - The **initial supply**is specified at contract's creation
  - The entire initial supply is held by the **contract's creator**
  - Token owners can **send tokens**to other addresses
- owner
- contract(initial supply)
![](/assets/smart-contracts-and-solidity-basics-problem-create-a-simple-token-01.png)


# Solution: Simple Token

```cs
contract SimpleToken {
  mapping (address => uint256) public balanceOf;

  function SimpleToken (uint256 initialSupply) public {
    balanceOf[msg.sender] = initialSupply;
  }

  function transfer(address to, uint256 value) public {
    if (balanceOf[msg.sender] >= value) && 
	(balanceOf[to] + value >= balanceOf[to]) {
    balanceOf[msg.sender] -= value; // Subtract the value from the sender
    balanceOf[to] += value; // Add the same value to the recipient
           }
  }
}
```



# Summary
- **Solidity** is a high-level programming language
  - Designed to write smart contracts in the Ethereum VM
- **Remix**is a powerful online Solidity IDE
- **Solidity programming**: contracts, functions, data types, arrays, maps, structs
![](/assets/smart-contracts-and-solidity-basics-summary-01.png)
![](/assets/smart-contracts-and-solidity-basics-summary-02.png)


# Resources
- Remix –  https://remix.ethereum.org
- Solidity official documentation – https://solidity.readthedocs.io/en/develop/
- Solidity tutorials – https://ethereumbuilders.gitbooks.io/guide/content/en/solidity_tutorials.html 
- Learn Solidity in Y Minutes – https://learnxinyminutes.com/docs/solidity/ 
- Solidity Code Style Guide – http://solidity.readthedocs.io/en/develop/style-guide.html 


<!-- # Resources -->
- https://ethereum.stackexchange.com
- https://github.com/OpenZeppelin/zeppelin-solidity/commit/370e6a882aef6b9600949594d3a3e4854260d51e
- https://medium.com/@jeff.ethereum/optimising-the-ethereum-virtual-machine-58457e61ca15
- http://www.blockchainexpert.uk/blog/what-is-solidity
- https://github.com/OpenZeppelin/zeppelin-solidity




