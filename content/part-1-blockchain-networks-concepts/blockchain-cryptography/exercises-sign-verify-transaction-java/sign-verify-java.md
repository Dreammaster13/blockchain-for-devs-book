# Exercises: Sign and Verify Transactions in Java

In this exercise, you shall write code on how to create random private key  public key  address and **sign** and **verify** transactions using the **secp256k1-based ECDSA** cryptography in Java. Your goal is to write code to **sign transactions** , given as **JSON** :

 ![](/assets/exercises-sign-verify-java-01.png)

You will use the following Java libraries and tools:

- **BouncyCastle** is a collection of APIs used in cryptography. It includes APIs for both the Java and the C# programming languages.
- **Google**  **Gson** is a Java library that can be used to convert Java Objects into their JSON representation. It can also be used to convert a JSON string to an equivalent Java object. Gson can work with arbitrary Java objects including pre-existing objects that you do not have source-code of.
- **Elliptic Curve Cryptography (ECC)** – public / private key cryptography based on the algebraic structure of elliptic curves over finite fields. The Elliptic-Curves Digital Signature Algorithm ( **ECDSA** ) provides signing by private key + verifying signature by public key.

 ![](/assets/exercises-sign-verify-java-02.png)

# 1. Create a new Maven Project with IntelliJIDEA

1. **Create** a new **Maven Project** from &quot;File&quot;&quot;New&quot;&quot;Project&quot;:

 ![](/assets/exercises-sign-verify-java-03.png)

1. **Choose**** name **of the project under &quot;ArtifactId&quot; and pick name for &quot;Groupid&quot;, then click Next/Finish until the** IDE** creates your project:

 ![](/assets/exercises-sign-verify-java-04.png)

1. After you have created successfully your project open **&quot;pom.xml&quot;** file in the root project directory and enter the following dependencies:

| \&lt; **dependencies** \&gt;
    \&lt; **dependency** \&gt;
        \&lt; **groupId** \&gt;org.bouncycastle\&lt;/ **groupId** \&gt;
        \&lt; **artifactId** \&gt;bcprov-jdk15on\&lt;/ **artifactId** \&gt;
        \&lt; **version** \&gt;1.54\&lt;/ **version** \&gt;
    \&lt;/ **dependency** \&gt;
    \&lt; **dependency** \&gt;
        \&lt; **groupId** \&gt;com.google.code.gson\&lt;/ **groupId** \&gt;
        \&lt; **artifactId** \&gt;gson\&lt;/ **artifactId** \&gt;
        \&lt; **version** \&gt;2.8.4\&lt;/ **version** \&gt;
    \&lt;/ **dependency** \&gt;
\&lt;/ **dependencies** \&gt; |
| --- |

1.
# 2.Implementation in JAVA

1. After you have installed the packages, create an empty class file in **src**** test ****java** :

 ![](/assets/exercises-sign-verify-java-05.png)

1. Create an inner class to represent **Transaction**** Object**:

 ![](/assets/exercises-sign-verify-java-06.png)

1. Within this main class create two utility methods to convert bytes to hex and vice-versa:

 ![](/assets/exercises-sign-verify-java-07.png)

1. Then create two methods which will calculate **RIPEMD160** and **SHA256** :

 ![](/assets/exercises-sign-verify-java-08.png)

 ![](/assets/exercises-sign-verify-java-09.png)

1. After you have wrote the utility methods, create two final variables for the **secp256k1** curve:

 ![](/assets/exercises-sign-verify-java-10.png)

1. Then, create a method, which will **generate**** random **EC key pair. By default,** the size is 256-bit**.

 ![](/assets/exercises-sign-verify-java-11.png)

1. To get the compressed public key from a given elliptic curve point, **get** the X and Y coordinates and convert them to BigInteger. Finally, return the **X** + **Y**&#39;s converted to integer **TestBit** (this method returns true if and only if the designated bit of this BigInteger is set).

 ![](/assets/exercises-sign-verify-java-12.png)

1. Then, create a method called **randomPrivateKeyToAddress,** which will create random private key public key address. To create the private key, **first** generate the random EC Pair and from it extract the private key:

 ![](/assets/exercises-sign-verify-java-13.png)

1. To get the public key, extract it from the **keyPair.** To get the compressed public key, use **encodeECPointHexCompressed** :

 ![](/assets/exercises-sign-verify-java-14.png)

1. Last but not least, to get the address calculate **RIPEMD160** on the compressed public key:

 ![](/assets/exercises-sign-verify-java-15.png)

1. Now **test** the method. Go to Main and call **randomPrivateKeyToAddress** :

 ![](/assets/exercises-sign-verify-java-16.png)

 ![](/assets/exercises-sign-verify-java-17.png)



1. Create a method called **signAndVerifyTransaction** , which will create a transaction from the given parameters, sign it by the sender and verify it with the sender&#39;s public key. The method will take a **recipient address** , **value** to send, **fee** , timestamp of the **date created** and the **sender&#39;s private key** in hexadecimal format:

 ![](/assets/exercises-sign-verify-java-18.png)

1. Get the private key in BigInteger from the hexadecimal:

 ![](/assets/exercises-sign-verify-java-19.png)

1. Before you continue, you need to create a method, which will **get the public key from the private** :

 ![](/assets/exercises-sign-verify-java-20.png)

1. Go back to the sign and verify method and **extract** the public key and address:

 ![](/assets/exercises-sign-verify-java-21.png)

1. Create a transaction object which will take sender address, recipient address, sender&#39;s compressed public&#39;s key, value, fee, date created. Later you will add the transaction&#39;s signature. Convert it into **JSON** format and calculate **SHA256** of the transaction to get its hash. Then, get the **transaction hash** by calculating the **SHA256** of the transaction:

 ![](/assets/exercises-sign-verify-java-22.png)

1. Then, **sign** the transaction with private key:

 ![](/assets/exercises-sign-verify-java-23.png)

The **SignData** method creates an **ECDsaSigner** ,which is initialized with **ECPrivateKeyParameters** from the private key and a true parameter which indicates that it will sign. **Generate** the signature and return it:

 ![](/assets/exercises-sign-verify-java-24.png)

1. Add the **signed transaction r** and **s** parameters and serialize it again:

 ![](/assets/exercises-sign-verify-java-25.png)

1. Another way to get the public key parameters from the hexadecimal private key:

 ![](/assets/exercises-sign-verify-java-26png)

1. To **verify** the transaction signature you need the public key, the transaction signature and the hash of the transaction:

 ![](/assets/exercises-sign-verify-java-27.png)

The **verifySignature** creates an **ECDsaSigner** , obtains the public key from private key ,initialized that it will not sign and with the public key. Then verifies the signature:

 ![](/assets/exercises-sign-verify-java-28.png)

1. That is the **signAndVerifyTransaction** method. Now test it with the following parameters:

**public static void** main(String[] args) **throws** Exception {

    _randomPrivateKeyToAddress_();
    _existingPrivateKeyToAddress_( **&quot;7e4670ae70c98d24f3662c172dc510a085578b9ccc717e6c2f4e547edd960a34&quot;** );

    _signAndVerifyTransaction_( **&quot;f51362b7351ef62253a227a77751ad9b2302f911&quot;** , 25000, 10, **&quot;2018-02-10T17:53:48.972Z&quot;** , **&quot;7e4670ae70c98d24f3662c172dc510a085578b9ccc717e6c2f4e547edd960a34&quot;** );
}

 ![](/assets/exercises-sign-verify-java-02.png)

# What to Submit?

Create a **ZIP file** (e.g. **username-sign-verify-**** java ****-exercise.zip** ) holding your .java file and the methods.
