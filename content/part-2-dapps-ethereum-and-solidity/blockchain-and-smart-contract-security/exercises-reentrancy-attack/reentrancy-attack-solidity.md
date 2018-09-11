# Exercises: Reentrancy Attack in Solidity Smart Contracts

This document describes the **exercise assignments** for the
[[\"Blockchain Academy\" course @ Software
University]{.underline}](https://softuni.bg/opencourses/blockchain-dev-course).
In this lesson we learned the **basics of Solidity** programming
language. The goal of this exercise is to get practical skills in
writing simple smart contracts in Solidity, publishing and testing
contracts in the Remix IDE.

1.  Create and Deploy HoneyPot Contract
    -----------------------------------

    1.  Go to <https://remix.ethereum.org>

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-012.png)

3.  Create the contract **HoneyPot**. Define the solidity version you
    want to compile the contract.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-013.png)

4.  The following code maps addresses to a value and store it in a
    public variable called balances. It allows to check the **HoneyPot**
    balance for an address.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-014.png)

5.  This is the constructor of the contract. The function with the same
    name as the contracts is the called constructor. It will be called
    when deploying the contract.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-015.png)

6.  The **put()** function below is where the storage of the ether value
    happens in the contract. Note that **msg.sender** here is the
    address from the sender of the transaction.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-016.png)

7.  The purpose of **get()** function is to let addresses to withdraw
    the value of ether they have in the **HoneyPot** balances.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-017.png)

8.  The unnamed function is called **fallback** function. It will only
    throw an exception if it is called.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-018.png)

2.  Create and Deploy HoneyPotCollect Contract
    ------------------------------------------

    9.  Create the contract **HoneyPotCollect**.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-019.png)

10. Define **HoneyPot** variable.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-02.png)

11. Then we define the constructor function. This is the function that
    is called when **HoneyPotCollect** is created. Note that we pass an
    address to this function. This address will be the **HoneyPot**
    contract address.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-03.png)

12. The **kill()** function destroys the **HoneyPotCollect** and send
    all ether containing in it to the address that calls the kill
    function.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-04.png)

13. The **collect()** function is the one that will set the **reentrancy
    attack** in motion. It puts some ether in **HoneyPot** and right
    after it gets it. The payable term here tells the **Ethereum Virtual
    Machine** that it permits to receive ether. Invoke this function
    with also some ether.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-05.png)

14. The last function is the **fallback** function. This unnamed
    function is called whenever the HoneyPotCollect contract receives
    ether.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-06.png)

3.  Exercise
    --------

    15. Then **"Start to compile"** the contacts.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-07.png)

16. Go to **"Run"** tab and choose for environment **"JavaScript VM"**.
    Firstly choose the **HoneyPot** contract and create it.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-09.png)

18. Then choose **HoneyPotCollect** contract, copy the **HoneyPot**
    contract address and paste it to create the contact.

![](/assets/exercises-reentrancy-attack-on-a-smart-contract-011.png)

After deploying HoneyPotCollect, call **collect()** and sending with it
some ether and debug the function.

**HoneyPot** **get()** function sends ether to the address that called
it only if this contract has any ether as balance. When **HoneyPot**
sends ether to **HoneyPotCollect** the fallback function is triggered.
If the **HoneyPot** balance is more than the value that it was sent to,
the fallback function calls **get()** function once again and the cycle
repeats.

Recall that within the **get()** function the code that sets the balance
to zero comes only after sending the transaction. This tricks the
**HoneyPot** contract into sending money to the **HoneyPotCollect**
address repeatedly until **HoneyPot** is depleted of almost all its
ether.

What to Submit?
===============

Create a **zip file** (e.g.
**your-username-honeypotcollect-attack.zip**) with the source code and
an image with an address with at least 100+ ethers.

Submit your **zip** file as **homework** at the course Web site.
