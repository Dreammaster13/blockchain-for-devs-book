# Exercises: Smart Contract Unit Testing with Truffle and Ganache

We are going to build a **contract** which allows for funds raising.
Mechanics are the same as a single Kickstarter campaign. There is a
particular time to reach the goal. If this does not happen, **donators**
are free to request a **refund** of transferred Ether. If a goal is
reached, the owner of the **smart** **contact** can withdraw funds. We
want to also allow for "**anonymous**" donation which is merely a
transfer of funds to a **smart contract**. Even if we are saying
anonymous, you need to know that all transactions are publicly visible
**Ether** **transfer**. We are just unable to refund those funds.

Original Source: [Michal
Zalecki](https://michalzalecki.com/ethereum-test-driven-introduction-to-solidity)

With clearly defined scope we can start implementing our smart contract

Setup
=====

**Truffle** is a popular development **framework** written in
**JavaScript**. It neither comes with any convention for your smart
contracts nor utility library but provides you with a local environment
for **developing**, **testing** and **deploying** **contracts**. For
starters, **install** **truffle** locally.

  -------------------------
  npm install --g truffle
  -------------------------

**Truffle** makes it possible to kick off the project using one of many
[boxes](http://truffleframework.com/boxes/). A box is a boilerplate
containing something more than just a necessary minimum. We are
interested in starting a new project from scratch.

  --------------
  truffle init
  --------------

Look around; there is not much there yet. The only interesting bit is a
**Migrations.sol** contract and its migration file. History of
migrations you are going to make over time is recorded on-chain through
a **Migrations** contract.

2.  Implementing the Contract and Tests
    ===================================

    1.  Setting an Owner
        ================

The first feature we want our **smart contract** to have is an
**owner**. Before we start writing the first **test** let's create an
empty **Funding contract** so our **tests** can compile.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-012.png)

Now, with an **empty** **contract** defined we can create a **testing
contract**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-017.png)

**Note**: Some **linters** will tell you that "**truffle/Assert.sol**"
doesn't exist. Just **ignore** this. **Truffle** will do his **magic**
and everything will be fine.

Now we are ready to **run** our first **test**.

  --------------
  truffle test
  --------------

**Note**: If this **doesn't work** you need to **rename** the
"**truffle.js**" to "**truffle-old.js**" in main folder.

Yay! If we got it right, contracts should **compile** **without** any
errors. But we still don't have any **tests**. We need to fix that. We
want **Funding** to **store** an **address** of its **deployer** as an
**owner**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-018.png)

Each **smart contract** has an **address**. An instance of each **smart
contract** is implicitly convertible to its **address** and
**this.balance** returns contract's balance. One smart contract can
instantiate another, so we **expect** that **owner** of Funding is still
the same **contract**. Now, to the **implementation**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-019.png)

A **sender** of the message inside a **constructor** is a **deployer**.
Let's **rerun** the **tests**!

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-022.png)

In **JavaScript**, we can require a contract using
**artifacts.require**. Instead of **describe** which you may know from
other testing frameworks we use **contract** which does some cleanup and
provides a list of **available accounts**. The first account is used by
default during tests.

Now let's **run** both **tests** **together**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-02.png)

Apart from creating a new **contract** during **tests**, we would also
like to **access contracts** deployed through a **migration**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-03.png)

It **fails** as we do not have any **migration** for our **Funding
contract**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-06.png)
===============================================================================================================================================

Accepting donations
-------------------

Next feature on the roadmap is accepting **donations**. Let's start with
a **test** in **Solidity**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-07.png)

We use a **unit** called **Finney**. You should know that the smallest,
indivisible **unit** of **Ether** is called **Wei** (it fits **uint**
type).

1 **Ether** is 10\^18 **Wei**

1 **Finney** is 10\^15 **Wei**

1 **Szabo** is 10\^12 **Wei**

1 **Shannon** is 10\^9 **Wei**

Initially, a **contract** has no spare ethers to transfer so we can set
an initial balance. Ten **Ether** is more than enough. Let's write an
equivalent **JavaScript** **test**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-011.png)

**Testing** with **JavaScript** gives us an ability to **test** for
**multiple different accounts**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-013.png)

For tracking a **balance** of particular user, we can use **mapping**.
We have to mark a **function** as **payable**, so it allows users to
**send** **Ethers** along with **function** **calls**.

![](/assets/exercise-develop-and-unit-test-smart-contracts-with-truffle-015.png)

What to Submit?
===============

Create a **zip file** (e.g.
**your-username**-**contracts-truffle-unit-tests-exercise.zip**) holding
the

**Source** **code** (**without** node\_modules folder) and
**screenshots** with your experiments. Make screenshots of the **unit
tests** results.

Submit your **zip** file as **homework** at the course Web site.
