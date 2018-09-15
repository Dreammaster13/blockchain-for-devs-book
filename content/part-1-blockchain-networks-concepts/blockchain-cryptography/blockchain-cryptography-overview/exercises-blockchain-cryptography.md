# Exercises: Blockchain Cryptography

In this exercise, you shall write code to play with popular
**cryptographic algorithms** using crypto libraries from your
programming languages. You shall calculate hashes, derive keys from
passwords, encrypt and decrypt messages, sign messages and verify
message signatures, derive blockchain addresses from ECC private keys.

Ethereum Signature Creator
--------------------------

Write a program to calculate an **Ethereum signature** \[**v**, **r**,
**s**\] by given **message** and **private key**. Use **secp256k1** ECC
crypto-library and programming language by choice.

**Input**: 256-bit **private key**, input text **message**.

**Output**: JSON document, holding the **signed message** +
**signature** \[**v**, **r**, **s**\].

```
+-----------------------------------+-----------------------------------+
| **Input**                         | **Output**                        |
+===================================+===================================+
| **Private key:**                  | {\"signature\":\"0xacd0acd4eabd1b |
|                                   | ec05393b33b4018fa38b69eba8f16ac3d |
| 97ddae0f3a25b92268175400149d65d68 | 60eec9f4d2abc127e3c92939e680b91b0 |
| 87b9cefaf28ea2c078e05cdc15a3c0a   | 94242af80fce6f217a34197a69d35edaf |
|                                   | 616cb0c3da4265b01\",\"v\":\"0x1\" |
| **Message:**                      | ,\"r\":\"0xacd0acd4eabd1bec05393b |
|                                   | 33b4018fa38b69eba8f16ac3d60eec9f4 |
| exercise-cryptography             | d2abc127e\",\"s\":\"0x3c92939e680 |
|                                   | b91b094242af80fce6f217a34197a69d3 |
|                                   | 5edaf616cb0c3da4265b\"}           |
+-----------------------------------+-----------------------------------+
```

Ethereum Signature to Address
-----------------------------

Write a program to find the **signer's Ethereum address** by given
**signed message** + **Ethereum signature** \[**v**, **r**, **s**\]. Use
**secp256k1** ECC crypto-library and programming language by choice.

**Input**: JSON document, holding the **signed message** + **signature**
\[**v**, **r**, **s**\].

**Output**: Ethereum address.

  **Input**                                                                                                                                                                                                                                                                                                                          **Output**
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------
  {\"signature\":\"0xacd0acd4eabd1bec05393b33b4018fa38b69eba8f16ac3d60eec9f4d2abc127e3c92939e680b91b094242af80fce6f217a34197a69d35edaf616cb0c3da4265b01\",\"v\":\"0x1\",\"r\":\"0xacd0acd4eabd1bec05393b33b4018fa38b69eba8f16ac3d60eec9f4d2abc127e\",\"s\":\"0x3c92939e680b91b094242af80fce6f217a34197a69d35edaf616cb0c3da4265b\"}   0xa44f70834a711F0DF388ab016465f2eEb255dEd0

Ethereum Signature Verifier
---------------------------

Write a program to **verify** the **Ethereum signature** \[**v**, **r**,
**s**\] of given **signed message** by given Ethereum **address**. Use
**secp256k1** ECC crypto-library and programming language by choice.

**Input**: JSON document, holding the **signed message** + **signature**
\[**v**, **r**, **s**\].

**Output**: valid / invalid.
```
+-----------------------------------+-----------------------------------+
| **Input**                         | **Output**                        |
+===================================+===================================+
| **Address:**                      | valid                             |
|                                   |                                   |
| 0xa44f70834a711F0DF388ab016465f2e |                                   |
| Eb255dEd0                         |                                   |
|                                   |                                   |
| **Signature:**                    |                                   |
|                                   |                                   |
| acd0acd4eabd1bec05393b33b4018fa38 |                                   |
| b69eba8f16ac3d60eec9f4d2abc127e3c |                                   |
| 92939e680b91b094242af80fce6f217a3 |                                   |
| 4197a69d35edaf616cb0c3da4265b01   |                                   |
|                                   |                                   |
| **Message:**                      |                                   |
|                                   |                                   |
| exercise-cryptography             |                                   |
+-----------------------------------+-----------------------------------+
| **Address:**                      | invalid                           |
|                                   |                                   |
| 0xa44f70834a711F0DF388ab016465f2e |                                   |
| Eb255dEd0                         |                                   |
|                                   |                                   |
| **Signature:**                    |                                   |
|                                   |                                   |
| 5550acd4eabd1bec05393b33b4018fa38 |                                   |
| b69eba8f16ac3d60eec9f4d2abc127e3c |                                   |
| 92939e680b91b094242af80fce6f217a3 |                                   |
| 4197a69d35edaf616cb0c3da4265b01   |                                   |
|                                   |                                   |
| **Message:**                      |                                   |
|                                   |                                   |
| exercise-cryptography             |                                   |
+-----------------------------------+-----------------------------------+
```

Bitcoin Address Generator (C\# Edition)
---------------------------------------

In this guided exercise you will generate a Bitcoin address in C\#.

1.  First you need to open Visual Studio 2017 or another C\# IDE.

2.  Then **File** -\> **New** -\> **Project** and select "**Console
    Application"** give name and **OK**

![](/assets/exercises-blockchain-cryptography-2-01.png)

3.  We give a default **hexHash** (alphanumeric) and calculate **Public
    Key** by the function HexToByte. Hex to Byte converts the
    Hexidecimal string to a byte array, it's simple as taking the 2
    characters and converting it into base 256.

4.  **Note:** The alphanumeric string is written by you, do not use the
    capital letters "O" and "I" because they are very similar looking to
    the numbers "0" and "1".

5.  You can use the following string:
    **"0450863AD64A87AE8A2FE83C1AF1A8403CB53F53E486D8511DAD8A04887E5B23522CD470243453A299FA9E77237716103ABC11A1DF38855ED6F2EE187E9C582BA6"**

![](/assets/exercises-blockchain-cryptography-2-012.png)

6.  We have to implement the **HexToByte** method and we need to add
    **using System.Globalization** because of the **NumberStyles** and
    **CultureInfo**

![](/assets/exercises-blockchain-cryptography-2-020.png)

7.  Then we need the **Sha256 Public Key**, so we have to implement the
    **Sha256** method.

![](/assets/exercises-blockchain-cryptography-2-021.png)

8.  Sha256 uses Microsoft's security cryptography include, and by
    default takes a byte array. We need **using
    System.Security.Cryptography;**

![](/assets/exercises-blockchain-cryptography-2-023.png)

10. Again this function uses Microsoft's security cryptography include
    and is pretty much identical to the **Sha256 function**.

![](/assets/exercises-blockchain-cryptography-2-024.png)

11. **AppendBitcoinNetwork** simply pre-appends a byte onto the
    beginning of an array of bytes and then hash the **PreHashWNetwork**
    with **Sha256**.

![](/assets/exercises-blockchain-cryptography-2-026.png)

13. Then hash the **Public Hash **

![](/assets/exercises-blockchain-cryptography-2-02.png)

14. Finally we need **concat address** which appends the last 4 bytes of
    the hash onto the end of the RipeMD160 value.

![](/assets/exercises-blockchain-cryptography-2-04.png)

16. It is Console Application so if we want to see the result we have to
    print it on the console. We have to the method **ByteToHex** which
    **converts a byte into a hexadecimal string.**

![](/assets/exercises-blockchain-cryptography-2-05.png)

17. The last method we need is the **Base58Encode** to make **the
    Contact Address** human readable and we have to add Reference
    **System.Numerics** and then **using System.Numerics** to use
    BigInteger.

18. **Note:** The alphanumeric string is written by you, do not use the
    capital letters "O" and "I" and the letter "l" the small letter of
    "L" and the number "0" because they are very similar looking to the
    numbers "0" and "1".

19. You can use the following string:
    **"123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz"**

![](/assets/exercises-blockchain-cryptography-2-07.png)

21. Now Run the Console Application (**CTRL + F5**) and the result
    should be the following:

![](/assets/exercises-blockchain-cryptography-2-08.png)

The full source code is available here:
<https://github.com/sMustafov/BitcoinAddressGeneratorCSharpEdition>

Bitcoin Address Generator (JS Edition)
--------------------------------------

Now we will generate **Bitcoin** address and transaction by using
**JavaScript** programming language.

1.  Firstly you will need **JS IDE** (**WebStorm**).

2.  Then Start the IDE and choose "**Create New Project**".

![](/assets/exercises-blockchain-cryptography-2-010.png)

4.  Click Right button on project folder and choose **New** -\>
    **JavaScript File.**

![](/assets/exercises-blockchain-cryptography-2-011.png)

5.  Open Command Line Interpreter go to the project folder and install
    **BitcoinJS library** there.

![](/assets/exercises-blockchain-cryptography-2-019.png)

6.Private Key to Bitcoin Address
--------------------------------

Write a program to generate a **Bitcoin address** by given **Bitcoin
private key** (WIF-encoded).

-   **Decode** the private key: from WIF to **256-bit number**.

-   Calculate the **public key** coordinates: **P(x, y)**.

-   Compress the public key **P** **P\_compressed**.

-   Generate the Bitcoin address:
    **Base58CheckEncode**(**RIPEMD160**(**SHA256**(**P\_compressed**))).

Compare your output with the output from <https://www.bitaddress.org>
\[Wallet Details\].

  **Input**                                             **Output**
  ----------------------------------------------------- ------------------------------------
  5HueCGU8rMjxEXxiPuD5BDku4MkFqeZyd4dZ1jvhTVqvbTLvyTJ   1GAehh7TsJAHuUAeKZcXf5CnwuGuGgyX2S

7. (Optional) Asymmetric Encryption / Decryption
------------------------------------------------

Write a program to **encrypt** / **decrypt** a **message** using **ECC**
with the **secp256k1** curve using the encryption scheme
[**ECIES**](https://en.wikipedia.org/wiki/Integrated_Encryption_Scheme)
(Elliptic Curve Integrated Encryption Scheme). Encryption will use EC
**public key** and decryption will use EC **private key**. Internally,
use AES-256-CTR.

-   Generate a EC **public** / **private** **key** pair using secp256k1.

-   Encrypt the **message** using the **public key**. Internally encrypt
    the message with AES-256-CTR, using as AES key the shared secret
    number S. Store as output the ECC point R + ciphertext + iv + hmac.

-   Decrypt the **message** using the **private key**. Internally use
    AES-256-CTR. From the ECC point R, using the private key, decode the
    shared secret number S, then using the AES parameters, decrypt the
    ciphertext.

-   As reference, you may follow this example:
    <https://github.com/planetbeing/bitcoin-encrypt/blob/master/bitcoin-encrypt.py>.

***Note***: some developers might find this problem very complicated, so
enjoy learning about ECC and AES from it. If you fail, just skip it, or
explore the sample implementation from the link below.

What to Submit?
===============

Create a **ZIP file** (e.g.
**your-name-blockchain-cryptography-exercise.zip**) holding your source
code for all problems. Submit your ZIP file as **homework** at the
course Web site.
