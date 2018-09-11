# Exercises: Install Ganache and Truffle Framework

The goal of this exercise is to install **Ganache** and **Truffle**.
**Truffle** is the most popular development framework for **Ethereum**
with a mission to make your life a whole lot easier. **Ganache** is part
of the **Truffle Suite**. It is one click blockchain, which allows you
to quickly fire up a **personal Ethereum blockchain**, which you can use
to run tests, execute commands, and inspect state while controlling how
the chain operates. Ganache simplifies **DApp** development by placing
your contracts and transactions front and center. Using Ganache, you can
quickly see how your application affects the blockchain, and introspect
details like your accounts, balances, contract creations and gas costs.
You can also fine tune Ganache\'s advanced mining controls to better
suit your needs.

Install in Linux
----------------

1.  **Truffle** requires **NodeJS** to be installed, so let's first get
    NodeJS. If you already have **NodeJS** go to step 6. In other case,
    continue reading. In order to install NodeJS, we just have to use
    the **apt package manager**. We should refresh our local package
    index first, and then install from the repositories. In Linux
    console type:

  ---------------------
  sudo apt-get update
  ---------------------

![](/assets/install-ganache-and-truffle-01.png)

2.  Now we are ready to install **NodeJS**. Type in console:

  -----------------------------
  sudo apt-get install nodejs
  -----------------------------

![](/assets/install-ganache-and-truffle-06.png)

3.  If the package in the repositories suits your needs, this is all you
    need to do to get set up with **Node.js**. In most cases, you will
    also want to install **npm**, which is the Node.js **package
    manager**. This will allow you to easily **install modules and
    packages** to use with Node.js.\
    To start installation type:

  --------------------------
  sudo apt-get install npm
  --------------------------

![](/assets/install-ganache-and-truffle-07.png)

4.  Now it is good idea to check which version of Node.js you have
    installed after these initial steps, type:

  -----------
  nodejs -v
  -----------

![](/assets/install-ganache-and-truffle-08.png)

5.  Update nodeJS.

+--------------------------------------------------------------------+
| > curl -sL https://deb.nodesource.com/setup\_8.x \| sudo -E bash - |
| >                                                                  |
| > sudo apt-get install -y nodejs                                   |
+--------------------------------------------------------------------+

6.  Now is time to install Ganache. Open
    <https://github.com/trufflesuite/ganache/releases/tag/v1.0.2> and
    select the appropriate version.

![](/assets/install-ganache-and-truffle-09.png)

7.  Download the file.

8.  The file you just saved is **AppImage. AppImages** can be downloaded
    and run without installation or the need for root rights. But first,
    you must make it executable file.

9.  On this purpose open console and type:

  ------------------------------------------
  chmod a+x ganache-1.0.2-x86\_64.AppImage
  ------------------------------------------

10. Now you can **run** the file with **double click**.

11. Now you can allow or not Ganache to analyze your data or not. Make a
    choice and click **continue**.

    ![](/assets/install-ganache-and-truffle-011.png)

12. **To install Truffle** open the console and type:

  -------------------------
  npm install --g truffle
  -------------------------

or

  ------------------------------
  sudo npm install --g truffle
  ------------------------------

if you have no write access to **/usr/local/lib/node\_modules**.

![](/assets/install-ganache-and-truffle-012.png)

Install in Windows
------------------

1.  To install Ganache in **Windows** environment you can use PowerShell
    to install the **Ganache.appx** package:

    ![](/assets/install-ganache-and-truffle-013.png)

**\
**

2.  ### **Or just go to** <https://github.com/trufflesuite/ganache/releases> and **download the exe file**. 

    ![](/assets/install-ganache-and-truffle-02.png)

    **Windows Defender SmartScreen** can warn you that this installation
    is not save. Just ignore it and follow the steps to install Ganache:

    ![](/assets/install-ganache-and-truffle-03.png)

After clicking the "More Info", a new screen will appear showing you the
installation button.

> ![](/assets/install-ganache-and-truffle-04.png)

Then you just need to click Next and follow the normal install
instruction and after that you should have Ganache installed on your
computer.

3.  To install **truffle** in Windows you can use **npm**

  ------------------------
  npm install -g truffle
  ------------------------

![](/assets/install-ganache-and-truffle-05.png)
