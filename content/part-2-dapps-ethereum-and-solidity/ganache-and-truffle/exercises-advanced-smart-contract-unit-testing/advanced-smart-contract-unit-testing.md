# Exercises: Advanced Smart Contract Unit Testing with Truffle and Ganache

Now let's extend even further our **Funding** **contract** and start
using some more **Solidity** **Specific** **unit** **testing**
mechanics. We need to make some **modification** to our files so we can
do this.

Original Source: [Michal
Zalecki](https://michalzalecki.com/ethereum-test-driven-introduction-to-solidity-part-2/)

Time constraint
---------------

Our donators can now **donate**, but there is **no** time constraint. We
would like users to send us some **Ether** but only until
**fundraising** is finished. We can get a current block timestamp by
reading now property. If you start writing **tests** in **Solidity**,
you will quickly realize that there is **no** easy way to **manipulate**
block time from the **testing smart contract**. There is also **no**
**sleep** method which would **allow** us to set a **tiny** duration,
wait for a second or two and try again **simulating** that time for
**donating** is up.

I have already mentioned that there is no easy way to **manipulate**
block time from **Solidity** (at least at the time of writing).
**JSON-RPC** is a **stateless**, **remote** procedure call **protocol**.
**Ethereum** provides multiple methods which we can remotely
**execute**. One of the use cases for it is creating **Oracles**. We are
not going to use **JSON-RPC** directly but through **Web3.js** which
provides a convenient abstraction for **RPC** **calls**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-012.png)

Calling **increaseTime** results in two **RPC** calls. You will not find
them on **Ethereum** wiki page. Both **evm\_increaseTime** and
**evm\_mine** are non-standard methods provided by **Ganache** -
blockchain for **Ethereum** **development** we use when running
**tests**.

We need to **modify** a lot of files to include the time in our
**contract** and **tests**. So let's start with our **migration** file.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-017.png)

Now let's change our Funding contract.
======================================

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-018.png)

Because we changed our **constructor** in the **Funding** **contract**
to accept duration we need to now to **pass** that **information** every
time we create an **instance**. To make this easier we will use the
"**beforeEach**" function that creates an **instance** before each
**test** for us and we need to **remove** **everywhere** that we created
**instance** our self.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-019.png)

**Repeat** this and **remove** this line **everywhere** and then add the
"**beforeEach**" as follow:

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-020.png)

Now we are ready with our **JavaScript** **testing** and we need to fix
the **Solidity** **testing** **contract** to work with our changes to
the **Funding** **contract**.

Again we need to **remove** **everywhere** where we made an **instance**
of **Funding** as we are going to use "**beforeEach**".

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-023.png)

Modifiers and testing throws
----------------------------

We can now tell whether **fundraising** finished, but we are not doing
anything with this information. Let's put a **limitation** on how long
people can **donate**.

Since **Solidity 0.4.13**, a **throw** is **deprecated**. New function
for handling state-reverting exceptions are **require()**, **assert()**
and **revert()**. You can **read** more about **differences** between
those calls here.

All exceptions **bubble** up, and there is no **try\...catch** in
**Solidity**. So how to test for **throws** using just **Solidity**?
Low-level call function returns **false** if an **error** occurred and
**true** otherwise. You can also use a [proxy
contract](http://truffleframework.com/tutorials/testing-for-throws-in-solidity-tests)
to achieve the same in what you may consider as more elegant way.

Let's add a new **test** to our **testing contract**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-02.png)

In **JavaScript** we can just use **try\...catch** to handle an
**error**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-03.png)

We can now **restrict** time for calling **donate** in **Funding**
contract with "**onlyNotFinished"** **modifier**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-05.png)

Withdrawal
----------

We accept **donations**, but it is **not** yet possible to **withdraw**
any funds. An **owner** should be able to do it only when the goal has
been reached. We also cannot set a goal. We would like to do it when
**deploying** a **contract** --- as we did when we were setting
**contract** **duration**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-06.png)

From **Solidity**, we are not able to select an address from which we
want to make a transaction. By design, address of the **smart contract**
is going to be used. What we can do to test withdrawal from an account
which is not an owner is to use deployed contract instead of using
created by a testing contract. Trying to withdraw in such case should
always fail. One restriction is that you cannot specify a constructor
params --- the migration script has already deployed this contract.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-07.png)
========================================================================================================================================

You might have noticed that JavaScript is a lot easier and less hacky
then a Solidity test case but we still have the nasty **try catch** and
a **regex**. This is because the available **assert.throws** does
**not** work well with **async** code.

Let's now Add the **functionality** to the **Funding** **contract**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-08.png)

We already store the **owner** of the contract. Restricting access to
particular functions using an **onlyOwner** **modifier** is a popular
convention. Popular enough to export it to a reusable piece of code but
we will cover this later. The rest of the code should not come as a
surprise, you have seen it all!

Now our new **tests** should be **passing**. Let's check to make sure.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-09.png)

Refund
------

Currently, funds are stuck, and **donators** are unable to **retrieve**
their **Ether** when a goal is not achieved within a specified time. We
need to make sure it is possible. Two conditions have to be met so users
can get their **Ether** back. Duration is set in a construct so if we
set a 0 duration contract is finished from the beginning, but then we
cannot donate to have something to withdraw. So we write tests for this
case solely in **JavaScript**.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-010.png)
========================================================================================================================================

**Implementing** **refund** function can be tricky. Our intuition may
tell us to loop through our **donators** and transfer them their
**funds**. **Problem** with this **solution** is that the more
**donators** we have the more **gas** to **pay** and it is not only
looping but also making multiple transactions. We would like to keep the
**cost** of running a function **low** and **predictable**. Let's just
allow each user to withdraw their donation.

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-011.png)

We would like to save the amount to transfer first and then zero the
balance. It is an **implementation** of the withdrawal pattern.
**Transfering** an amount straight from the balances **mapping**
introduces a security risk of **re-entrancy** --- **calling** **back**
**multiple** **refunds**.

Now it is time to **check** our **tests**.
![](/assets/exercise-solidity-specific-unit-testing-with-truffle-013.png)

Code Coverage
-------------

1.  We should probably add code coverage reporting to our project, so
    that we can see how much of the code is "touched" by our tests. But
    first you should install **Python 2.7** and **Git** if you haven't
    already! You might need to install **Windows-Build-Tools** with
    "**npm install windows-build-tools**"

2.  After that, open a command line, go to your project's folder, and
    type:

  npm init -y
  -------------------------------------------
  npm install \--save-dev solidity-coverage

3.  This also includes a **special fork of Ganache** for code coverage
    testing. You should update your **truffle-config.js** to accommodate
    this:

    ![](/assets/exercise-solidity-specific-unit-testing-with-truffle-014.png)

4.  Now let's **copy** this **scripts** and **add** them to our
    **package.json**.

+-----------------------------------------------------------------------+
| > \"scripts\": {                                                      |
| >                                                                     |
| > \"test\": \"truffle test\",                                         |
| >                                                                     |
| > \"test:run:server\": \"testrpc-sc \--port 8555 -l 0xfffffffffff -g  |
| > 0x01\",                                                             |
| >                                                                     |
| > \"test:coverage\": \"solidity-coverage\"                            |
| >                                                                     |
| > },                                                                  |
+-----------------------------------------------------------------------+

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-015.png)

5.  In your main project folder (where truffle-config.js is located)
    create a file called **.solcover.js** (watch the dot in the
    beginning), with the following content:

  -----------------------------------
  module.exports = { norpc: true };
  -----------------------------------

6.  Let's run our Special Ganache server:

  -------------------------
  npm run test:run:server
  -------------------------

7.  Now to run your tests you should use the following command:

  -----------------------
  npm run test:coverage
  -----------------------

Here is the **final** result:

![](/assets/exercise-solidity-specific-unit-testing-with-truffle-016.png)

**Congratulations**, you have all features **implemented** and decent
**test** **coverage**.

Conclusion
----------

An important takeaway from this Exercise is to think twice before
deciding when to **test** **smart contracts** using **JavaScript** and
when using **Solidity**. The rule of thumb is that **smart contracts**
interacting with each other should be **tested** using **Solidity**. The
rest can be tested using **JavaScript**, it is just easier.
**JavaScript** testing is also closer to how you are going to use your
contracts from the client application. Well written test suit can be a
useful resource on how to interact with your **smart contracts**.

What to Submit?
===============

Create a **zip file** (e.g.
**your-username-truffle-solidity-specific-unit-tests-exercise.zip**)
holding the

**Source** **code** (without **node\_modules** folder) and
**screenshots** with your experiments. Make screenshots of the **unit
tests** results.

Submit your **zip** file as **homework** at the course Web site.
