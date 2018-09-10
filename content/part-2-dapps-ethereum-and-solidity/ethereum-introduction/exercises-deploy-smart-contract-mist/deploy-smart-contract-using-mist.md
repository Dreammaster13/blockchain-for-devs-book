# Exercises: Deploy a Solidity Smart Contract using Mist

In this exercise, use **geth** and **Mist** to deploy a smart contract
and play with it.

Deploy and Invoke Contract
--------------------------

1.  Start **geth**.

    ![](/assets/exercises-deploy-smart-contract-mist-01.png)

2.  Start **Mist**.

3.  Go to **"Contracts"** tab and click **"Deploy new contract"**.

    ![](/assets/exercises-deploy-smart-contract-mist-01.png)

4.  Choose the account from which you want to deploy the contract.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

5.  Write this code to **"Solidity Contract Source Code"**:
```cs
+-----------------------------------------------------------------------+
| pragma solidity ^0.4.18;                                              |
|                                                                       |
| contract MyToken {                                                    |
|                                                                       |
| /* This creates an array with all balances */                         |
|                                                                       |
| mapping (address => uint256) public balanceOf;                        |
|                                                                       |
| uint256 public totalSupply;                                           |
|                                                                       |
| /* Initializes contract with initial supply tokens to the creator of  |
| the contract */                                                       |
|                                                                       |
| function MyToken() public {                                           |
|                                                                       |
| totalSupply = 100000;                                                 |
|                                                                       |
| balanceOf[msg.sender] = totalSupply; // Give the creator all          |
| initial tokens                                                        |
|                                                                       |
| }                                                                     |
|                                                                       |
| /* Send coins */                                                      |
|                                                                       |
| function transfer(address _to, uint256 _value) public {               |
|                                                                       |
| require(balanceOf[msg.sender] >= _value); // Check if the sender      |
| has enough                                                            |
|                                                                       |
| require(balanceOf[_to] + _value >= balanceOf[_to]); // Check          |
| for overflows                                                         |
|                                                                       |
| balanceOf[msg.sender] -= _value; // Subtract from the sender          |
|                                                                       |
| balanceOf[_to] += _value; // Add the same to the recipient            |
|                                                                       |
| }                                                                     |
|                                                                       |
| }                                                                     |
+-----------------------------------------------------------------------+
```
It is very basic **token contract** which have **totalSupply** =
**1000000** and function **"Transfer"** to transfer tokens between
accounts.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

6.  You can create the token faster or cheaper. Click **"Deploy"**.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

7.  Then write your password and **"Send Transaction"**.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

8.  You can see your transaction at **"Wallets"** tab.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

9.  This is the information about the transaction.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

10. You should wait until the transaction is mined.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

11. Then go to the **"Contracts"** tab and choose the token you created.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

12. It should look like this.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

13. Go and copy your Main accounts address (account which created the
    contract).

![](/assets/exercises-deploy-smart-contract-mist-01.png)

14. Paste the address to **"balanceOf**" place and it should
    have 100000. All the tokens go to the creator address balance.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

15. Go and copy the second account.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

16. It should have 0 tokens balance.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

17. Select the only function of the token -- **"Transfer"** and paste
    the second address to the **"to"** place and the amount to send to
    **"value"** place (e.g. 256 tokens). Choose the account to execute
    (Main account which have tokens) and **"Execute"**.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

18. Write your password and **"Send Transaction"**.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

19. You can see your transaction.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

20. After it is ready you will see the following window:

![](/assets/exercises-deploy-smart-contract-mist-01.png)

21. This is the information for the transaction:

![](/assets/exercises-deploy-smart-contract-mist-01.png)

22. Go again to the token and paste the main account address. You should
    see the following. The balance of the main account should be 999744
    (after 256 sent).

![](/assets/exercises-deploy-smart-contract-mist-01.png)

23. And account 2 should have 256 tokens.

![](/assets/exercises-deploy-smart-contract-mist-01.png)

What to Submit?
===============

Create a **zip file** (e.g. **username-deploy-smart-contract-mist.zip**)
holding the screenshots of the token balances.

Submit your **zip** file as **homework** at the course Website.

![](/assets/exercises-deploy-smart-contract-mist-01.png)
