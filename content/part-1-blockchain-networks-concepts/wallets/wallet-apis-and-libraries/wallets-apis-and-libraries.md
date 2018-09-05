# Wallet Standards, Wallet APIs and Libraries

## Hierarchical Wallets, BIP39 and BIP44, Keystores, Popular Wallet Libraries
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-01.png)
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-02.png)
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-03.png)
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-04.png)
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-05.png)
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-06.png)
![](/assets/wallet-apis-and-libraries-hierarchical-wallets-bip39-and-bip44-keystores-popular-wallet-libraries-07.png)




# Table of Content
- **Keystores** for Private Keys
  - The JSON / UTC Keystore Format
- Hierarchical Wallets (**HD Wallets**)
  - Mnemonics and BIP39
  - BIP44 and Key Derivation
- Crypto-Wallet **Libraries**
  - Nethereum, NBitcoin, QBitNinja, Ethers.js
![](/assets/wallet-apis-and-libraries-table-of-content-01.png)
![](/assets/wallet-apis-and-libraries-table-of-content-02.png)


# **Keystores** for Private Keys

```cs
Keystores, Encryption, JSON / UTC Format
```

![](/assets/wallet-apis-and-libraries-keystores-for-private-keys-01.png)


# Ways to Store Secret Keys in Wallets 
- Store a **private key offline**
  - Paper wallet: holds **address**+ **private key**
- Store a **mnemonic phrase offline** (mostly used)
  - One **mnemonic phrase**keeps all private keys
- **Keystore file**(UTC / JSON)
  - Strongly encrypted by a **password** (e.g. Scrypt + AES)
  - Keystore files use a **standard format**&rarr; easy export / import
  - Can keep **encrypted mnemonic**and **private keys**(MetaMask)
![](/assets/wallet-apis-and-libraries-ways-to-store-secret-keys-in-wallets-01.png)
![](/assets/wallet-apis-and-libraries-ways-to-store-secret-keys-in-wallets-02.png)
![](/assets/wallet-apis-and-libraries-ways-to-store-secret-keys-in-wallets-03.png)


# The JSON / UTC Keystore Format
- **The JSON / UTC keystore** format is widely used in the Ethereum ecosystem, e.g. by **geth** and **MyEtherWallet**:
  - https://github.com/ethereum/wiki/wiki/Web3-Secret-Storage-Definition

```cs
Example: https://gist.github.com/nakov/53f869e01c9b573844c48e5966e33a3f 
```

![](/assets/wallet-apis-and-libraries-the-json-utc-keystore-format-01.png)




# The JSON / UTC Keystore Format
- The usual **naming convention**is **<uuid>.json**
  - **<uuid>**is the **128-bit UUID** given to the secret key
- **AES-128-CTR** is now the minimal requirement
  - Other symmetric cyphers might be used, e.g. **AES-256-CBC**
- The key-derivation function **PBKDF2** must be supported by **all minimally-compliant implementations**
  - Other key-derivation functions: **Scrypt**, **Argon2**, **Bcrypt**

```cs
"kdf": "pbkdf2"
```



# Other Wallet Formats
- **WIF** – wallet import format (Bitcoin)
  - https://en.bitcoin.it/wiki/Wallet_import_format
  - Holds unencrypted private key (bad idea!) as Base58-encoded text
- **PKCS#12** – encrypted keystore archive (**.p12** / **.pfx** file)
  - Holds encrypted SafeBags, holding keys, certificates, other assets
  - http://www.pkiglobe.org/pkcs12.html
- **Windows CryptoAPI**Next Generation (CNG) Keystore
  - https://msdn.microsoft.com/en-us/library/windows/desktop/bb204778.aspx 


<!-- # Hierarchical Wallets (HD Walle -->

```cs
Mnemonics, BIP39, Key Derivation, BIP44
```

![](/assets/wallet-apis-and-libraries-hierarchical-wallets-hd-wallets-01.png)


# BIP-32, BIP-39 and BIP-44 Standards
- **BIP-32** describes how to build a **hierarchical wallet** (**HD wallet**)
- **BIP-39** describes how to encode a root key as **mnemonic phrase**
  - And the process of transforming the mnemonic words into a **512-bit seed** used later for generating a **BIP-32 HD wallet**
- **BIP-44** proposes a **specific hierarchy** for key derivation
  - **BIP-44** is a specific format of a **BIP-32 wallet**
  - List of registered **coin types**for **BIP-44**
    - **https://github.com/satoshilabs/slips/blob/master/slip-0044.md**


# HD Wallet: Key Derivation

```cs
cheese upset pudding inmate flavor crushhard same element index laugh supreme
```

- The **wallet app**generates random **mnemonic words**
- Which then are used by the **BIP-39 specification**to derive the **512-bit seed**
- Which is used as **BIP-32 seed** to generate the **BIP-32 root key** (**master key**)
- Used to derive the **child key**by derivation path (like **m/44'/0'/0'/0/0**), which gives the **private key** and the **address** 


# BIP-44 Coin Types
- BIP44 Constants JS Library
  - github.com/bitcoinjs/bip44-constants 
- Registered **coin types**in the **BIP-44** standard:

```cs
npm i --save bip44-constants 
```





# Popular Crypto-Wallet **Libraries**

```cs
Nethereum, NBitcoin, QBitNinja, Ethers.js
```

![](/assets/wallet-apis-and-libraries-popular-crypto-wallet-libraries-01.png)


# Nethereum
- **Nethereum** is the **.NET integration library**for **Ethereum**
- Simplifying the smart contract interaction and access to **Ethereum** nodes like **Geth**, **Parity** and **Quorum**
  - Nethereum.**Signer** – ECC crypto-functions using the **secp256k1**
  - Nethereum.**Web3**– interaction with Ethereum via **RPC**
  - Nethereum.**Geth** – extended Web3 library for **Geth**
  - Nethereum.**Parity** – extended Web3 library for **Parity**
  - Nethereum.**Quorum** – extension to interact with **Quorum**


# Installing and Using Netehreum
- Install the "**Nethereum**" package from **NuGet**
- Import the **Nethereum**namespaces:
- **Example**: recover a HD wallet from **mnemonic phrase**

```cs
using Nethereum;
```



# Nethereum – Examples 
- **Example**: create a new random HD wallet
- **Example**: derive addresses and print them at the console


<!-- # Nethereum – Examples -->
- **Example**: send Ethereum **transaction**


# NBitcoin
- **NBitcoin** is a powerful **Bitcoin library for C# :**
  - **https://github.com/MetacoSA/NBitcoin** 
- Implements all most relevant **BIPs**
  - **https://github.com/bitcoin/bips**
- Provides low level access to **Bitcoin primitives**
  - Implements Bitcoin transaction builder, RPC client, REST client
- BIP-39 mnemonics + BIP-32 **HD wallet**support


# NBitcoin
- Include the**NBitcoin** library
- Generate a random **private key**
- Export the private key in Wallet Import Format (**WIF**)

```cs
using NBitcoin;
```



# NBitcoin
- Derive a **public** **key** from the private key:
- Generate a Bitcoin address from the **public key**:

```cs
PubKey publicKeyTestNet = testNetPrivateKey.PubKey;
Console.WriteLine(publicKeyTestNet);
```



# QBit Ninja
- **QBit Ninja**== open-source **API**to query the Bitcoin blockchain
  - Documentation: **https://qbitninja.docs.apiary.io**
- Retrieve / broadcast transactions as **JSON** or **byte[]**
![](/assets/wallet-apis-and-libraries-qbit-ninja-01.png)


# Ethers.js
- **Ethers.js**– a client-side JS wallet library (for Ethereum)
  - Documentation: https://docs.ethers.io/ethers.js
- Installing the **ethers.js** library using **npm**:
- Including the library in a JS project:

```cs
npm install --save ethers
```



# Ethers.js: Private Keys, Wallets, Addresses
- From private key to Ethereum address:
- Create a new **random wallet**

```cs
let privateKey =
  "0x012345678901234567890123456789012345678901234567890123456789012";
let wallet = new ethers.Wallet(privateKey);
console.log("Address: " + wallet.address);
// Address: 0x1C68340bb2810BF5B0BEd3EDE256335cb51C53C7
```



# Ethers.js – Mnemonics and Brain Wallets
- From **mnemonic phrase**to private key to Ethereum address
- From **brain wallet**to Ethereum address:

```cs
let mnemonic = "enact range stone boss alone october list vast laptop sunny iron price";
let wallet = ethers.Wallet.fromMnemonic(mnemonic);
console.log("Address: " + wallet.address);
// Address: 0xa05dfb7868d5cdf655d775DA7C96269ba54AC4a4
```



# Summary
- Major techniques to keep a private key:
  - Save the**plain private key**, save a **mnemonic phrase**,use an encrypted **keystore file (UTC / JSON)**
- **BIP-32** describes how to build a **hierarchical wallet**
  - **BIP-39** describes how to derive **seed**from **mnemonics**
  - **BIP-44** described how to **hierarchically derive keys**
- **Nethereum** is the **C#** **integration** **library** for **Ethereum**
- **NBitcoin** is the **Bitcoin** **library**for**C#**
- **Ethers.js**helps creation of **client-side** **JavaScript** **based** **wallets**
![](/assets/wallet-apis-and-libraries-summary-01.png)


# Wallet APIs and Libraries
- http://www.kingsland.academy


# Resources
- The JSON / UTC Keystore Format:  https://github.com/ethereum/wiki/wiki/Web3-Secret-Storage-Definition 
- BIP32: https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki
- BIP39: https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki 
- BIP44: https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki 
- Mnemonic Code Converter: https://freewallet.org/bip39-recovery-from-mnemonic-bitcoin-and-other-cryptocurrencies 
- Nethereum: https://github.com/Nethereum/Nethereum, http://nethereum.com/ 
- NBitcoin: https://github.com/MetacoSA/NBitcoin,https://programmingblockchain.gitbooks.io/programmingblockchain/content/  
- How to make your first transaction with Nbitcoin: https://www.youtube.com/watch?v=X4ZwRWIF49w
- Qbit Ninja: https://qbitninja.docs.apiary.io/#
- Ethers.js: https://docs.ethers.io/ethers.js/html/ 




