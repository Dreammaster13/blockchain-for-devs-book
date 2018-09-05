# Exercises: Building a Very Simple Blockchain Network

In this exercise you will learn how **Blockchain networks** work by building a simple one in Python. **Blockchain** is an immutable, sequential chain of records called **blocks**. Blocks can hold **transactions** , documents, files or any data you like, really, but the important thing is that blocks are chained together using hashes. The blockchain networks consists of interconnected **nodes** which update the blocks together using a **consensus algorithm** (like proof-of-work). Original source: [https://hackernoon.com/learn-blockchains-by-building-one-117428612f46](https://hackernoon.com/learn-blockchains-by-building-one-117428612f46).

You will need **Python 3.6+** , **Python IDE** and HTTP client like **Postman** or **cURL**. Also, you will need to install the **Flask** Requests Library for Python.

1. 1.Install Python and Flask

To **install Python** and all required libraries in Windows, use the steps below:

1.
  1. If you have installed Python, you can skip this step. If not, go to python website: [https://www.python.org/downloads/](https://www.python.org/downloads/) and download &quot; **Python 3.6**&quot; or later. Then install it.

 ![](/assets/exercises-building-a-blockchain-01.png)
 
1.
  1. Choose the [**Customize installation**] link.

 ![](/assets/exercises-building-a-blockchain-02.png)
1.
  1. Check all the options and click [**Next**].

 ![](/assets/exercises-building-a-blockchain-03.png)

Check also the **&quot;Add Python to environment variables&quot;** (by default it is not checked) and click [Install].

 ![](/assets/exercises-building-a-blockchain-04.png)

1.
  1. After completing open Command Line Interpreter and write the command: &quot; **python -V**&quot;. You should see the Python version. Note the capital &quot; **V**&quot;.
  2. Then install the &quot; **Flask**&quot; library using the command:

| pip install Flask==0.12.2 requests==2.18.4 |
| --- |

1. 2.Install Postman

We will need also **Postman** HTTP client as we mention it above.

1. Go to the official Postman web site: [https://www.getpostman.com](https://www.getpostman.com), download and install Postman.

 ![](/assets/exercises-building-a-blockchain-05.png)
 
1. After installing it, you should sign up (it is free).

 ![](/assets/exercises-building-a-blockchain-06.png)

1. After signing up you will see the following window. You can close the inner one.

 ![](/assets/exercises-building-a-blockchain-07.png)
 
1. Finally you should see window like this one below:

 ![](/assets/exercises-building-a-blockchain-08.png)
 
1. Now we have all we need to start writing and testing the code.

1. 3.Building Our Blockchain

1. Firstly, open your favorite text editor or Python IDE (e.g. **PyCharm** ).
2. Create a new file, called &quot; **blockchain.py****&quot;**.
  - If you are new to Python, remember to **never mix tabs with spaces**.
  - You may get errors like this &quot;TabError: inconsistent use of tabs and spaces in indentation&quot;.
  - Use **4 tabs** for indenting code blocks.
3. We will create a **Blockchain** class whose constructor creates an initial **empty list** to store our **blockchain** , and another to store **transactions**. Here is how it will look like:

 ![](/assets/exercises-building-a-blockchain-09.png)

1. This is how does a **block** looks like:

 ![](/assets/exercises-building-a-blockchain-10.png)

Each **Block** has an **index** , a **timestamp** , **a list of transactions** , **a proof** and the **hash of the previous Block**.

1. Now we will create the method **new\_transaction()** which will add the new transactions to the block.

 ![](/assets/exercises-building-a-blockchain-11.png)
 
After **new\_transaction()** adds a **transaction** to the list, it returns the index of the block which the transaction will be added to—the next one to be mined.

When our **Blockchain** is instantiated, we&#39;ll need to seed it with a **genesis block** —a block with no predecessors. We&#39;ll also need to add a &quot;proof&quot; to our genesis block which is the result of mining (or proof of work).

 ![](/assets/exercises-building-a-blockchain-12.png)
 
1. In addition to creating the **genesis block** in our constructor, we&#39;ll also flesh out the methods for **new\_block()**, **new\_transaction()** and **hash()**.  Now we will create the **new\_block()** and **hash()** functions.
2. Firstly we should import some libraries to the class.

 ![](/assets/exercises-building-a-blockchain-13.png)

1. Then we will implement the **new\_block()** function.

 ![](/assets/exercises-building-a-blockchain-14.png)
 
1. We now have blocks and we should implement**last\_block()**function to be able to see the last block.

 ![](/assets/exercises-building-a-blockchain-15.png)

1. And the **hash()** function should look likethis:

 ![](/assets/exercises-building-a-blockchain-16.png)

1. We should import:

| from uuid import uuid4 |
| --- |

1. Now the implementation of basic **proof-of-work** algorithm:

 ![](/assets/exercises-building-a-blockchain-17.png)

1. Proof of work method implemented. Now we need a condition for validating the proof.

 ![](/assets/exercises-building-a-blockchain-18.png)

To adjust the difficulty of the algorithm, we could modify the number of leading zeroes. But 4 is sufficient. You&#39;ll find out that the addition of a single leading zero makes a huge difference to the time required to find a solution.

Our class is almost complete and we are ready to begin interacting with it using **HTTP requests**.

1. 4.Exposing a Blockchain API

We&#39;re going to use the **Python Flask Framework**. It&#39;s a micro-framework and it makes it easy to map endpoints to Python functions. This allows us talk to our **Blockchain** over the web using **HTTP requests**.

We&#39;ll create three API endpoints:

- **/transactions/new** – to create a new transaction to a block
- **/mine** – to tell our server to mine a new block.
- **/chain** – to return the full blockchain.

Let&#39;s set up the **Flask** framework.

1. We need the following import:

| from flask import Flask, jsonify, request |
| --- |

1. Firstly, we instantiate our **node**.
2. Then create a random name for our node.
3. And instantiate out the **Blockchain** class.

 ![](/assets/exercises-building-a-blockchain-19.png)

1. Create the **/mine** endpoint, which is a **GET** request.
2. Create the **/transactions/new** endpoint, which is a **POST** request, since we&#39;ll be sending data to it.
3. Create the **/chain** endpoint, which returns the full blockchain.
4.
8.Runs the server on port **5000**. ![](/assets/exercises-building-a-blockchain-20.png)

1. We will implement the **new\_transaction()**function:

 ![](/assets/exercises-building-a-blockchain-21.png)

1. It is time to implement the **mine()**function:

1.
  1. Calculate the Proof of Work

 ![](/assets/exercises-building-a-blockchain-22.png)

1.
  1. Reward the miner (us) by adding a transaction granting us 1 coin

 ![](/assets/exercises-building-a-blockchain-23.png)

1.
  1. Add the new block to the chain and forget it

 ![](/assets/exercises-building-a-blockchain-24.png)

1. 5.Implementing a Consensus Algorithm

So far, we&#39;ve got a basic **Blockchain** that accepts **transactions** and allows us to **mine** new **blocks**.

But the whole point of **blockchains** is that they should be **decentralized**. Now we&#39;ll have to implement a **Consensus Algorithm** if we want more than one node in our network.

1. Each node on our network should keep a **registry** of other nodes on the network. Thus, we&#39;ll need some more endpoints:

- **/nodes/register** – to accept a list of new nodes in the form of URLs.
- **/nodes/resolve** – to implement our Consensus Algorithm, which resolves any conflicts – to ensure a node has the correct chain.

1. We&#39;ll need to modify our **Blockchain&#39;s constructor** and provide a method for registering nodes:

1. We should add to the constructor:

| self.nodes = set() |
| --- |

1. We should import:

| from urllib.parse import urlparse |
| --- |
|   |

And the **register\_nodes()**method:

 ![](/assets/exercises-building-a-blockchain-25.png)

1. We should import:

| import requests |
| --- |

We&#39;ll make the rule that the longest valid chain is authoritative. In other words, the longest chain on the network is the de-facto one.Using this algorithm, we **reach consensus** amongst the nodes in our network.

1. The first method **valid\_chain()** is responsible for checking if a chain is valid by looping through each block and verifying both the hash and the proof.

 ![](/assets/exercises-building-a-blockchain-26.png)

1. The method **resolve\_conflicts()**loops through all our neighboring nodes, downloads their chains and verifies them using the above method.
  - If a valid chain is found, whose length is bigger than ours, we replace ours.

 ![](/assets/exercises-building-a-blockchain-27.png)

1. Let&#39;s **register** the two endpoints to our **API** , one for adding neighboring nodes and the another for resolving conflicts:

1. First the **register\_nodes()** function:

 ![](/assets/exercises-building-a-blockchain-28.png)

1. Then the **consensus()**function:

 ![](/assets/exercises-building-a-blockchain-29.png)

1. Finally, to run the app you will need this method:

 ![](/assets/exercises-building-a-blockchain-30.png)

At this point you can grab a **different machine** if you like, and spin up **different nodes** on your **network**. Or spin up processes using **different ports** on the **same machine**.

- It is easier to spin up another node on your machine, on a different port, and register it with your current node.
- Thus, you will have two nodes: [http://localhost:5000](http://localhost:5000) and [http://localhost:5001](http://localhost:5001).

1. 6.Interacting with our Blockchain

1. Now open command shell and go to your project file directory.
2. Start your first blockchain node:

Run the command:

| python blockchain.py |
| --- |

If everything is OK you will see the following result:

| \* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit) |
| --- |

1. Now open **Postman**.
2. Let&#39;s try **mining a block** by making a GET request to[http://localhost:5000/mine](http://localhost:5000/mine). It should look like this:

 ![](/assets/exercises-building-a-blockchain-31.png)

1. The result should be:

 ![](/assets/exercises-building-a-blockchain-32.png)

1. Let&#39;s **create a new transaction** by making a **POST** request to [http://localhost:5000/transactions/new](http://localhost:5000/transactions/new) with a body containing our transaction JSON structure:

 ![](/assets/exercises-building-a-blockchain-33.png)

1. The result should be:

 ![](/assets/exercises-building-a-blockchain-34.png)

1. Let&#39;s **inspect the full chain** by requesting [http://localhost:5000/chain](http://localhost:5000/chain).

 ![](/assets/exercises-building-a-blockchain-35.png)

1. The result should be like this:

 ![](/assets/exercises-building-a-blockchain-36.png)

1. Register a new node:

 ![](/assets/exercises-building-a-blockchain-37.png)

1. **Do not forget** to run another node with port 5001 on your machine
2. The result should be:

 ![](/assets/exercises-building-a-blockchain-38.png)

1. Finally resolve conflicts:

 ![](/assets/exercises-building-a-blockchain-39.png)

1. The result should be:

 ![](/assets/exercises-building-a-blockchain-40.png)

# 2.What to Submit?

Create a **zip file** (e.g. **your-name-own-blockchain-exercise.zip** ) holding the source codefiles like **blockchain.py**.

Submit your zip file as **homework** at the course Web site.