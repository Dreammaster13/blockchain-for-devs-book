# Exercises: Sign and Verify Transactions in Python

In this exercise, you shall write code on how to **sign** and **verify** transactions using the **secp256k1-based ECDSA** cryptography in Python. You will write code to **sign transactions** , given as **JSON** :

 ![](/assets/exercises-sign-verify-python-01.png)

You will use the following libraries:

- **pycoin** – Python Cryptocoin Utilities
- **hashlib** – secure hashes and message digests

 ![](/assets/exercises-sign-verify-python-02.png)

1.
# 1.Implement and Test the Code

1. First, import the necessary dependencies:

 ![](/assets/exercises-sign-verify-python-03.png)

1. Then, create two methods, which will be used later. The first one is **ripemd160** cryptographic hash function by a given string produces a 160-bit output. Return the hash in hex format.

 ![](/assets/exercises-sign-verify-python-04.png)

1. Then, create a method that calculates **sha256** of a given string.

 ![](/assets/exercises-sign-verify-python-05.png)

1. Since the **sign** transaction method will take a private key in hex format, you will have to **extract** its address in order to add it to the transaction itself. But first, step by step. Create the following method:

 ![](/assets/exercises-sign-verify-python-06.png)

Then from the private key, build a key pair from using **generator\_secp256k1** :

 ![](/assets/exercises-sign-verify-python-07.png)

From the generated key pair, **extract** the compressed public key:

 ![](/assets/exercises-sign-verify-python-08.png)

Last but not least, a method that by a given public key returns the address using **ripemd160** :

 ![](/assets/exercises-sign-verify-python-09.png)

1. Create a method that takes private key and returns extracted public key and address:

 ![](/assets/exercises-sign-verify-python-10.png)

1. The **sign** and **verify** method will take arguments needed to build a transaction with the following format:

1.
  - Sender address: 40 hex digits
  - Recipient address: 40 hex digits
  - Sender public key: 65 hex digits
  - Transfer value: integer
  - Mining fee: integer
  - Date created: ISO-8601 string

 ![](/assets/exercises-sign-verify-python-11.png)

In the method, extract the public compressed key and the address from the private key:

 ![](/assets/exercises-sign-verify-python-12.png)

Then create the transaction object and **stringify** it

 ![](/assets/exercises-sign-verify-python-13.png)

Calculate **sha256** of the transaction JSON:

 ![](/assets/exercises-sign-verify-python-14.png)

Sign the transaction with the imported **sign** method that takes the **secp256k1** , private key and the hash as arguments.

 ![](/assets/exercises-sign-verify-python-15.png)

Add the transaction signature to the transaction itself:

 ![](/assets/exercises-sign-verify-python-16.png)

Again, JSON encode the transaction:

 ![](/assets/exercises-sign-verify-python-17.png)

1. Last but not least, verify the transaction using the imported **verify** method that takes the **secp256k1** , public key, transaction hash and the transaction signature. Return whether the transaction is valid or not:

 ![](/assets/exercises-sign-verify-python-18.png)

1. **Test** the method with the following input:

| sign\_and\_verify\_transaction(
    recipient\_address= **&quot;f51362b7351ef62253a227a77751ad9b2302f911&quot;** ,
    value=25000,
    fee=10,
    date\_created= **&#39;2018-02-10T17:53:48.972Z&#39;** ,
    sender\_priv\_key\_hex= **&quot;7e4670ae70c98d24f3662c172dc510a085578b9ccc717e6c2f4e547edd960a34&quot;** ) |
| --- |

 ![](/assets/exercises-sign-verify-python-02.png)

# What to Submit?

Create a **ZIP file** (e.g. **username**** - ****sign-verify-python**** -exercise.zip**) holding your Python file and the methods.