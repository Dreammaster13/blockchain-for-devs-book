# Exercises: Sign and Verify Transactions in C#

In this exercise, you shall write code on how to create random private key  public key  address and **sign** and **verify** transactions using the **secp256k1-based ECDSA** cryptography in C#. You will **sign transactions** , given as **JSON** :

 ![](/assets/exercises-sign-verify-csharp-01.png)

You will use the following .NET Core libraries to simplify your work:

- **BouncyCastle** is a collection of APIs used in cryptography. It includes APIs for both the Java and the C# programming languages.
- **Newtonsoft.Json** is popular high-performance JSON framework for .NET by Newtonsoft. You can serialize and deserialize any .NET object with Json.NET&#39;s powerful JSON serializer. Also create, parse, query and modify JSON using Json.NET&#39;s JObject, JArray and JValue objects and so on.
- **Elliptic Curve Cryptography (ECC)** - Public / private key cryptography based on the algebraic structure of elliptic curves over finite fields. The Elliptic-Curves Digital Signature Algorithm ( **ECDSA** ) provides signing by private key + verifying signature by public key.

 ![](/assets/exercises-sign-verify-csharp-02.png)

# 1. Create Project and Import Packages

**Create** a .NET Core App and **install** the following **NuGetPackages** :

 ![](/assets/exercises-sign-verify-csharp-03.png)

# 2. Implementation in C#

1. After you have installed the packages, create two utility methods to convert bytes to hex and vice-versa:

 ![](/assets/exercises-sign-verify-csharp-04.png)

 ![](/assets/exercises-sign-verify-csharp-05.png)

1. Then create two methods which will calculate **RIPEMD160** and **SHA256** :

 ![](/assets/exercises-sign-verify-csharp-06.png)

 ![](/assets/exercises-sign-verify-csharp-07.png)

1. After you have wrote the utility methods, create two readonly variables for the **secp256k1** curve:

 ![](/assets/exercises-sign-verify-csharp-08.png)

1. Then, create a method, which will **generate**** random** EC key pair. By default, the size is 256-bit.

 ![](/assets/exercises-sign-verify-csharp-09.png)

1. To get the compressed public key from a given elliptic curve point, **get** the X and Y coordinates and convert them to BigInteger. Finally, return the **X** + **Y**&#39;s converted to integer **TestBit** (this method returns true if and only if the designated bit of this BigInteger is set).

 ![](/assets/exercises-sign-verify-csharp-10.png)

1. Then, create a method called **RandomPrivateKeyToAddress,** which will create random private key public key address. To create the private key, **first** generate the random EC Pair and from it extract the private key:

 ![](/assets/exercises-sign-verify-csharp-11.png)

1. To get the public key, extract it from the **keyPair.** To get the compressed public key, use **EncodeECPointHexCompressed** :

 ![](/assets/exercises-sign-verify-csharp-12.png)

1. Last but not least, to get the address calculate **RIPEMD160** on the compressed public key:

 ![](/assets/exercises-sign-verify-csharp-13.png)

1. Now **test** the method. Go to Main and call **RandomPrivateKeyToAddress** :

 ![](/assets/exercises-sign-verify-csharp-14.png)



1. Create a method called **SignAndVerifyTransaction** , which will create a transaction from the given parameters, sign it by the sender and verify it with the sender&#39;s public key. The method will take a **recipient address** , **value** to send, **fee** , timestamp of the **date created** and the **sender&#39;s private key** in hexadecimal format:

 ![](/assets/exercises-sign-verify-csharp-15.png)

1. Get the private key in BigInteger from the hexadecimal:

 ![](/assets/exercises-sign-verify-csharp-16.png)

1. Before you continue, you need to create a method, which will **get the public key from the private** :

 ![](/assets/exercises-sign-verify-csharp-17.png)

1. Go back to the sign and verify method and **extract** the public key and address:

 ![](/assets/exercises-sign-verify-csharp-18.png)

1. Create a transaction which will take sender address, recipient address, sender&#39;s compressed public&#39;s key, value, fee, date created. Later you will add the transaction&#39;s signature. Convert it into **JSON** format and calculate SHA256 of the transaction to get its hash. Then, get the **transaction hash** by calculating the **SHA256** of the transaction:

 ![](/assets/exercises-sign-verify-csharp-19.png)

1. Then, **sign** the transaction with private key:

 ![](/assets/exercises-sign-verify-csharp-20.png)

The **SignData** method creates an **ECDsaSigner** ,which is initialized with **ECPrivateKeyParameters** from the private key and a true parameter which indicates that it will sign. **Generate** the signature and return it:

 ![](/assets/exercises-sign-verify-csharp-21.png)

1. Add the **signed transaction r** and **s** parameters and serialize it again:

 ![](/assets/exercises-sign-verify-csharp-22.png)

1. Another way to get the public key parameters from the hexadecimal private key:

 ![](/assets/exercises-sign-verify-csharp-23.png)

1. To **verify** the transaction signature you need the public key, the transaction signature and the hash of the transaction:

 ![](/assets/exercises-sign-verify-csharp-24.png)

The **VerifySignature** creates an **ECDsaSigner** , initialized that it will not sign and with the public key. Then verifies the signature:

 ![](/assets/exercises-sign-verify-csharp-25.png)

1. That is the **SignAndVerifyTransaction** method. Now test it with the following parameters:

| SignAndVerifyTransaction(                recipientAddress: &quot;f51362b7351ef62253a227a77751ad9b2302f911&quot;,                value: 25000,                fee: 10,                iso8601datetime: &quot;2018-02-10T17:53:48.972Z&quot;,                senderPrivKeyHex: &quot;7e4670ae70c98d24f3662c172dc510a085578b9ccc717e6c2f4e547edd960a34&quot;            ); |
| --- |

 ![](/assets/exercises-sign-verify-csharp-26.png)

# What to Submit?

Create a **ZIP file** (e.g. **username-sign-verify-**** c# ****-exercise.zip** ) holding your C# file and the methods.