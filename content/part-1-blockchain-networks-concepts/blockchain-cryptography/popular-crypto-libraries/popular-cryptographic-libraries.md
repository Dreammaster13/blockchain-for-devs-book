# Popular Cryptographic Libraries for JavaScript, Python, Java and C#

# Table of Contents
- Cryptography in **JavaScript**
  - ECDSA, elliptic.js, js-sha3.js
- Cryptography Libraries in **Python**
  - ECDSA, eth_keys
- **Java** Cryptography
  - JCA, Bouncy Castle, Web3j
- C# and **.NET**Cryptography
  - Bouncy Castle .NET, Nethereum
![](/assets/popular-crypto-libraries-table-of-contents-01.png)
![](/assets/popular-crypto-libraries-table-of-contents-02.png)
![](/assets/popular-crypto-libraries-table-of-contents-03.png)
![](/assets/popular-crypto-libraries-table-of-contents-04.png)
![](/assets/popular-crypto-libraries-table-of-contents-05.png)


# Cryptography in JavaScript
- ECDSA with elliptic.js and js-sha3
![](/assets/popular-crypto-libraries-cryptography-in-javascript-01.png)
![](/assets/popular-crypto-libraries-cryptography-in-javascript-02.png)








# Cryptography in Python
- Hashes, ECC and ECDSA, eth_keys Library
![](/assets/popular-crypto-libraries-cryptography-in-python-01.png)
![](/assets/popular-crypto-libraries-cryptography-in-python-02.png)


# ECDSA in Python: Generate / Load Keys

```cs
import eth_keys, eth_utils, binascii, os

# privKey = eth_keys.keys.PrivateKey(os.urandom(32))
privKey = eth_keys.keys.PrivateKey(binascii.unhexlify( '97ddae0f3a25b92268175400149d65d6887b9cefaf28ea2c078e05cdc15a3c0a'))
pubKey = privKey.public_key
pubKeyCompressed = '0' + str(2 + int(pubKey) % 2) + str(pubKey)[2:66]
address = pubKey.to_checksum_address()
print('Private key (64 hex digits):', privKey)
print('Public key (plain, 128 hex digits):', pubKey)
print('Public key (compressed):', pubKeyCompressed)
print('Signer address:', address)
```



# ECDSA in Python: Sign Message

```cs
msg = b'Message for signing'
msgHash = eth_utils.keccak(msg)
signature = privKey.sign_msg(msg)

print('Msg:', msg)
print('Msg hash:', binascii.hexlify(msgHash))
print('Signature: [v = {0}, r = {1}, s = {2}]'.format(
  hex(signature.v), hex(signature.r), hex(signature.s)))
print('Signature (130 hex digits):', signature)
```



# ECDSA in Python: Verify Signature

```cs
msg = b'Message for signing'
msgSigner = '0xa44f70834a711F0DF388ab016465f2eEb255dEd0'
signature = eth_keys.keys.Signature(binascii.unhexlify( '6f0156091cbe912f2d5d1215cc3cd81c0963c8839b93af60e0921b61a19c54300c71006dd93f3508c432daca21db0095f4b16542782b7986f48a5d0ae3c583d401'))
signerPubKey = signature.recover_public_key_from_msg(msg)
print('Signer public key (recovered):', signerPubKey)
signerAddress = signerPubKey.to_checksum_address()
print('Signer address:', signerAddress)
print('Signature valid?:', signerAddress == msgSigner)
```



# Cryptography in Java
- JCA, Bouncy Castle and Web3j:Hashes, ECC and ECDSA
![](/assets/popular-crypto-libraries-cryptography-in-java-01.png)
![](/assets/popular-crypto-libraries-cryptography-in-java-02.png)


# JCA, Bouncy Castle and Web3j
- Cryptography in Java is based on the Java Cryptography Architecture (JCA)
  - Typical Java style: lot of boilerplate code
- **Bouncy Castle**is the leading Java cryptography library
  - Docs: https://www.bouncycastle.org/documentation.html
- **Web3j** – a simplified library for Ethereum and secp256k1
  - Web3j – https://github.com/web3j
  - The cryptographic functionality is in web3j/crypto


# ECDSA in Java: Install the Crypto Libraries
- This **Maven** dependency will install the following libraries:
  - **org.web3j.crypto**– Ethereum style secp256k1 EC cryptography
  - **org.bouncycastle**– BouncyCastle crypto provider for Java

```cs
<dependency>
  <groupId>org.web3j</groupId>
  <artifactId>crypto</artifactId>
  <version>3.3.1</version>
</dependency>
```



# ECDSA in Java: Initialize the Application

```cs
import org.bouncycastle.util.encoders.Hex;
import org.web3j.crypto.*;
import java.math.BigInteger;
```



# ECDSA in Java: Generate / Load Keys

```cs
// Generate random private key
// BigInteger privKey = Keys.createEcKeyPair().getPrivateKey(); 

BigInteger privKey = new BigInteger(
 "97ddae0f3a25b92268175400149d65d6887b9cefaf28ea2c078e05cdc15a3c0a", 16);
BigInteger pubKey = Sign.publicKeyFromPrivate(privKey);
ECKeyPair keyPair = new ECKeyPair(privKey, pubKey);

System.out.println("Private key: " + privKey.toString(16));
System.out.println("Public key: " + pubKey.toString(16));
System.out.println("Public key (compressed): " +
  compressPubKey(pubKey));
```



# ECDSA in Java: Sign Message

```cs
String msg = "Message for signing";
byte[] msgHash = Hash.sha3(msg.getBytes());
Sign.SignatureData signature =
  Sign.signMessage(msgHash, keyPair, false);

System.out.println("Msg: " + msg);
System.out.println("Msg hash: " + Hex.toHexString(msgHash));
System.out.printf(
  "Signature: [v = %d, r = %s, s = %s]\n",
  signature.getV() - 27,
  Hex.toHexString(signature.getR()),
  Hex.toHexString(signature.getS()));
```



# ECDSA in Java: Verify Signature

```cs
BigInteger pubKeyRecovered =
  Sign.signedMessageToKey(msg.getBytes(), signature);
System.out.println("Recovered public key: " +
  pubKeyRecovered.toString(16));

boolean validSig = pubKey.equals(pubKeyRecovered);
System.out.println("Signature valid? " + validSig);
```



# Cryptography in C# and .NET
- Bouncy Castle .NET and Nethereum:Hashes, ECC and ECDSA
![](/assets/popular-crypto-libraries-cryptography-in-c-and-net-01.png)
![](/assets/popular-crypto-libraries-cryptography-in-c-and-net-02.png)


# .NET Cryptography and Bouncy Castle .NET
- Cryptography in C# and .NET is based on:
  - The build-in libraries: **System.Security.Cryptography**
  - The **Bouncy Castle .NET**– a powerful C# cryptography library
    - http://www.bouncycastle.org/csharp 
- **Nethereum** – a simplified library for Ethereum and secp256k1
  - Nethereum – https://github.com/Nethereum
  - The cryptographic functionality is in Nethereum.Signer
  - Nethereum also includes the Bouncy Castle .NET library


# ECDSA in C#: Initialize the Application
- Install the "**Nethereum.Signer**" package from **NuGet**
- Import the **Nethereum Signer**namespaces:
- The **Bouncy Castle**namespaces will also be available, e.g.

```cs
using Nethereum.Signer;
using Nethereum.Signer.Crypto;
using Nethereum.Util;
using Nethereum.Hex.HexConvertors.Extensions;
```









# Summary
- **JavaScript** and **Python** provide simple cryptography libraries
  - Hashes, ECC, ECDSA, AES, and many more
- Cryptography in **Java** is heavy
  - **JCA** and **Bouncy Castle** are hard to use
  - **Web3j** is simplifies library for secp256k1
- Cryptography is **C#** is heavy
  - Use **Bouncy Castle .NET** for general crypto
  - Or **Nethereum** for simplified secp256k1
![](/assets/popular-crypto-libraries-summary-01.png)
![](/assets/popular-crypto-libraries-summary-02.png)




