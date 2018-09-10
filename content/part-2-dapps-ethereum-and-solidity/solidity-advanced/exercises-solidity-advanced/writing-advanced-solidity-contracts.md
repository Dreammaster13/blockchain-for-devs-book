# Exercises: Writing Advanced Solidity Smart Contracts

This document describes the **exercise assignments** for the
[[\"Blockchain Academy\" course @ Software
University]{.underline}](https://softuni.bg/opencourses/blockchain-dev-course).
In this lesson, we learned about functions, modifiers, events,
contracts, interactions, error handling and libraries in **Solidity**
programming language. The goal of this exercise is to get practical
skills in writing advanced smart contracts in Solidity, publishing and
testing contracts in the Remix IDE.

Receiving Funds from the default contract function
--------------------------------------------------

Create a Deposit contract which:

-   Stores the owner of the contract

-   People can **deposit** ethers in the contract

-   People can **get** the balance of the contract

-   Owner can **send** amount

    -   Upon sending, the contract self-destructs with the total amount
        in the contract

Use **modifiers** where it is appropriate.

Add appropriate **events** for the functions.

Inheritance
-----------

Write a **SafeMath** **contract** (don't google for the solution!)

-   The contract has **methods to safely add, subtract and multiply**
    two numbers

-   The methods should throw if an integer overflow occurs!

Write an **Owned contract**

-   Which knows its owner

-   Has method to change the owner (called from current owner)

-   Implements an access modifier

Write a **contract** that inherits **SafeMath** and **Owned** and uses
their methods

-   The contract should hold one **int256 state variable**

-   Has a method to **change the state variable** automatically by these
    rules:

    -   Method is **called by the owner**

    -   The state is incremented by **now % 256**

    -   The state is **multiplied by the amount of seconds since the
        last state change** (initially 1)

    -   The current **block gas limit is subtracted** from the state

Simple Bank
-----------

Create a simple Bank contract which:

-   holds balances of users

-   holds the owner of the contract

-   function **deposit** -- user deposits ether to the bank

    -   method must be **payable**

    -   use **require** to validate corner cases (e.g. overflow)

    -   **return** the balance of the user

-   function **withdraw(amount)** -- user withdraws ether from the bank

    -   use **require** to validate corner cases

    -   use **msg.sender.transfer**

    -   **return** the new balance of the user

-   function **getBalance** -- returns the caller\'s balance

Use **modifiers** where it is appropriate.

Add appropriate **events** for the functions.

A Simple Timed Auction
----------------------

Write a contract for an auction, which continues for **1 minute** after
the contract is deploye. Use **block.timestamp** as a start time.

Contract stores:

-   owner of the contract

-   start time

-   duration time

-   stores each buyer\'s amount bought

-   constructor with a parameter -- tokens amount to sell

-   function **buyTokens(amount)** -- **check** whether the auction has
    ended

Use **modifiers** where it is appropriate.

Add appropriate **events** for the functions.

A Simple Timed Auction (2)
--------------------------

Write a contract for an auction, which continues for 1 **block** after
contract\'s creation.

Hunger Games
------------

![](/assets/exercises-solidity-advanced-01.png)

Every year, in the ruins of what was once North America, the **Capitol**
of the nation of **Panem** - a technologically advanced, utopian city
where the nation\'s most wealthy and powerful citizens live, forces each
of its 12 districts to send a teenage boy and a girl, between the ages
of 12 and 18, to compete in the **Hunger Games**: a nationally televised
event in which \'tributes\' fight each other within an arena, until one
survivor remains.

This time of the year has come and it's time for the 100th hunger game
where you should send the new pair of teenage boy and girl.

Create a **Capitol** contract which:

-   **adds** person by **age** and **gender** (hint: use **struct** for
    storing the person)

-   **chooses** one girl and one boy:

<!-- -->

-   you are not allowed to choose the two people from the same gender

-   they should be between **12** and **18** years old

-   they should be chosen by **random** function (you can use
    **block.timestamp** but it is not safe or **oraclize** -\> learn
    more about it from oraclize documentation)

<!-- -->

-   you can **check how many girls and boys** are added -\> returns a
    **positive number**

-   after choosing the pair (boy and girl) set the **start date** of the
    hunger games and the **end date** (the hunger games should **last
    5** minutes)

-   after the **end** of the hunger game, **check** if the boy and girl
    are alive (use **random** 0 - dead, 1 - alive, use **modifier** for
    checking if the hunger game ended)

Use **modifiers** where it is appropriate.

Add appropriate **events** for the functions.

Test and play around with the contract!

 Pet Adoption
-------------

![](/assets/exercises-solidity-advanced-02.png)

In our adoption sanctuary, we have 5 kinds of animals

-   Fish

-   Cat

-   Dog

-   Rabbit

-   Parrot

The sanctuary **will store** information for all the people who have
adopted a pet.

After creating the contract, we should add the owner of the adoption
sanctuary.

Create a contract called **PetSanctuary** that has:

-   function **add** (animalKind, howManyPieces) -- **only** the owner
    can give shelter to animals in the sanctuary

-   function **buy** (personAge, personGender, animalKind)

<!-- -->

-   save when the animal is bought

-   you can only adopt **one** animal for lifetime

-   **Men** can only buy dog and fish

-   **Women** can buy from every kind, but if they are under 40, they
    are not allowed to buy a cat

-   function **giveBackAnimal**(animalKind)

<!-- -->

-   you can give the animal back in the first 5 minutes after adoption

<!-- -->

-   Think about how to store people's information in the contract.

Use **modifiers** where it is appropriate.

Add appropriate **events** for the functions.

(Optional) Lemonade Crowdsale
-----------------------------

![](/assets/exercises-solidity-advanced-03.png)

Have you heard about the kids who are selling lemonade at their stand
for BTC? Due to their success and good earnings, they are thinking about
expansion and migrate on the Ethereum Blockchain. They have heard about
the trend of **ICOs** and decided to launch their own. They are looking
for someone to help them with their campaign -- especially with writing
and deploying their **Lemon Token**. You are the perfect person to help
them! As a reward you will be paid in Lemon Tokens!

Create a **LemonToken** contract, which will be an ERC20Basic Token
Standard:

  -------------------------------------------------------------------------------
  contract **ERC20Basic** {\
  function **totalSupply()** public view returns (uint256);\
  function **balanceOf(address who)** public view returns (uint256);\
  function **transfer(address to, uint256 value)** public returns (bool);\
  event **Transfer(address indexed from, address indexed to, uint256 value)**;\
  }

  -------------------------------------------------------------------------------

-   name = \"**LemonToken**\";

-   symbol = \"**LMN**\";

-   decimals = **18**

-   initialSupply = **1 000 000** tokens with 18 decimals

Create a **LemonCrowdsale** contract, which will:

-   have **startTime**, **endTime**, **rateOfTokensToGivePerEth**,
    **walletToStoreTheEthers** and **lemonToken** as a reward

-   store how much **weiAmout** is contributed as a persistent variable

-   function **buyTokens()** -\> **payable**

    -   check if the purchase is valid **within the period**

    -   you are not allowed to buy zero tokens

    -   it should calculate the tokens buy the
        **rateOfTokensToGivePerEth** and **wei** **contributed** and
        **transfer** them to the balance of the contributor

    -   finally **forward the weiAmount to the wallet**

-   function **hasEnded()**

    -   to check if the crowdsale has ended -\> returns **bool**

<!-- -->

-   Use **modifiers** where it is appropriate

-   Add appropriate **Events** for the functions

Test and play around with the contract.

(Optional) CryptoZombies
------------------------

![](/assets/exercises-solidity-advanced-04.png)

CryptoZombies is a free, interactive code school that teaches you to
build games on Ethereum. The course is designed for beginners to
Solidity and starts with the absolute basics. Go to
<https://cryptozombies.io> and complete the 6 lessons.

What to Submit?
===============

Create a **zip file** (e.g. **username-solidity-advanced.zip**) holding
the **.sol** files from problems above.

Submit your zip file as **homework** at the course Web site.
