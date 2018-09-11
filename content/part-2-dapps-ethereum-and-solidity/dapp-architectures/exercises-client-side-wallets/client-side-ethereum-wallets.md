# Exercises: Using a Client-Side Ethereum Wallet  in the Web Browser

In this exercise, we will create an **HD Wallet** using **ethers.js** --
a complete Ethereum wallet implementation and library in JavaScript. Its
functionality will be -- **create** a wallet from random mnemonic
phrase, **open** wallet **from mnemonic phrase**, **open** wallet **from
JSON file**, **show** **mnemonic**, **show** the first **5 addresses and
their balances** and **send transaction**. The wallet will be **stored
in the local storage** of the browser in an **encrypted** **JSON**
format, which will **require a password** in order to be **decrypted**
and be **used**. We will use **ethers.js**, **jQuery** and
**jquery.qrcode** -- a jQuery plugin for a pure browser QR code
generation.

![](/assets/exercises-client-side-wallets-ethersjs-01.png)

Setup the Project
-----------------

**Download** the Skeleton zip file from today\'s topic and extract it.
**Open** the project. **Open** the HTML in the browser. **Get to know
the code**.

You will see that the HTML, CSS and dependency libraries are done and
downloaded, only the JavaScript file with the interesting methods are
left with TODOs. Now it is time to **implement** the TODO methods.

![](/assets/exercises-client-side-wallets-ethersjs-012.png)

Creating a Wallet
-----------------

**First**, we will start with creating a new wallet from random mnemonic
phrase, **encrypt** it with a provided password and **save** it in the
local storage.

![](/assets/exercises-client-side-wallets-ethersjs-022.png)

The method bound behind the **\[Generate Now\]** button is
**generateNewWallet**. Take the value of the password input with jQuery
and save it in a variable. Then use to ethers to create a new random
wallet -- **ethers.Wallet.createRandom(\[options\])**. Finally yet
importantly, use the **encryptAndSaveJSON** method to encrypt the wallet
and save it in the local storage.

Since **encryptAndSaveJSON** is not implemented, let\'s go and implement
it. As we can see, the method takes a **wallet** and a **password**. Use
**wallet.encrypt(password \[ , options\] \[, progressCallback\])** to
encrypt the wallet. Set options to be empty and call
**showLoadingProcess** method as a progressCallback. As a return
callback, the encrypt method returns the encrypted json, which we will
save in the local storage and call **showLoggedInButtons --** method if
there\'s a saved wallet in the local storage to show new available
functionality. Of course, catch errors and show them with **showError**
and finally hide the loading bar with **hideLoadingBar.**

![](/assets/exercises-client-side-wallets-ethersjs-023.png)

Now that the method is implemented, go back to **generateNewWallet**.
Call **encryptAndSaveJSON** and as a return callback **show** message
with the wallet mnemonic in order to users to save it if they want using
**showInfo(msg)** and write the result json in the textbox.

![](/assets/exercises-client-side-wallets-ethersjs-024.png)

Now, **open** the HTML, click **\[Create New Wallet\]**, **type** a
password and click **\[Generate Now\].**

![](/assets/exercises-client-side-wallets-ethersjs-026.png)

As you can see, the wallet is saved in the local storage encrypted and
now you can additional functionality. Let\'s implement **\[Delete
Wallet\]**, which will delete the wallet from the local storage and
return to either create new, open with mnemonic or open with file.
Method **deleteWallet** clears the local storage and shows the Home
view.

![](/assets/exercises-client-side-wallets-ethersjs-027.png)

Open Wallet
-----------

Next step is to open a wallet from a mnemonic. Open the HTML and check
the **\[Open Wallet From Mnemonic\]** section. There is a textarea for
the mnemonic, a password to encrypt it, a button to call the
**openWalletFromMnemonic** method and a textarea showing the result
json. Go to **openWalletFromMnemonic** method. First, take the value of
the mnemonic textarea with jQuery using its id. Then, using
**ethers.HDNode.isValidMnemonic(mnemonic)** validate whether the given
mnemonic is valid. Create a wallet from the mnemonic with
**ethers.Wallet.fromMnemonic(mnemonic)** and save the provided password
in a variable. Then, call **encryptAndSaveJSON** and as a result show a
message "Wallet successfully loaded!" and show the json in the second
textarea.

![](/assets/exercises-client-side-wallets-ethersjs-028.png)

Open the HTML, go to \[Open Wallet From Mnemonic\], get a mnemonic
phrase or something not valid, type a password and click **\[Open
Wallet\]**.

![](/assets/exercises-client-side-wallets-ethersjs-03.png)

Now, let's open a wallet from a file. The idea behind this is pretty
simple: Read the file and try to decrypt it with a provided password. If
the decryption is successful, save the read file in the local storage,
else -- show an error.

**Keep in mind that this wallet implementation takes only JSON files
that have a stored mnemonic in them!**

First, let's write the **decryptWallet** method which takes a json and a
password, and returns a wallet. Use
**ethers.Wallet.FromEncryptedWallet(json, password
\[,progressCallback\])**.

![](/assets/exercises-client-side-wallets-ethersjs-04.png)

Now go to **openWalletFromFile**. Use **FileReader** to read the file as
text. Onload, take the result -- the json and decrypt it using the
provided password. After the wallet is decrypted, check whether it has a
stored mnemonic in it. If there is not, return an Error: "Invalid JSON
file". If it is valid, save it in the local storage and show a message
"Wallet successfully loaded!". Use catch for any error and hide the
loading progress bar when completed.

![](/assets/exercises-client-side-wallets-ethersjs-05.png)

Now, open the HTM, go to **\[Open Wallet From File\]**, choose a file
and a password for decrypting it and click **\[Open\]**.

For example, take the two wallets provided in the skeleton -- one is a
JSON with no mnemonic and the other one has. Both of them are encrypted
with an empty password.

![](/assets/exercises-client-side-wallets-ethersjs-07.png)

Show Mnemonic
-------------

After that we have created/opened a HD wallet and have saved it in the
local storage, by a given password we can access it and get the mnemonic
in case we want to write it down or import it in another wallet. Go to
**showMnemonic** method. By a given password, we will decrypt the stored
in the local storage json and show the mnemonic.

![](/assets/exercises-client-side-wallets-ethersjs-08.png)

Go to **\[Show Mnemonic\]**, type the necessary password and click
**\[Show Mnemonic\]**

![](/assets/exercises-client-side-wallets-ethersjs-09.png)

View Addresses and their Balances
---------------------------------

Now we will show the first 5 addresses of the wallets, their balances
and a QR code of the address. We will decrypt the json, create an HDNode
from the mnemonic, derive 5 consecutive addresses by a given derivation
path, get for each one of them its ropsten ETH and visualize them. As
you know, hierarchical deterministic wallet represents a large tree of
private keys, which can reliably be reproduced from an initial seed.
Each node in the tree is represented by an HDNode, which be descended
into.

Go to **showAddressesAndBalances** in wallet.js. Take the provided
password, the json from the local storage and decrypt it. After it is
decypted, we will render the addresses and balances in a div with an id
**\#divAddressesAndBalances**.

![](/assets/exercises-client-side-wallets-ethersjs-010.png)

Now we will create the method **renderAddressesAndBalances**. Since we
use it only in this **showAddressesAndBalances**, you can create it in
the method. The method will take the decrypted wallet as a parameter.
Create an HDNode with **ethers.HDNode.fromMnemonic(mnemonic)**. To
derive from the node, use **derivePath(path)** (use **derivationPath**
variable) and build a wallet from the new one\'s private key **(new
ethers.Wallet(privateKey, provider))**. Use the constant variable in the
beginning of wallet.js. Then, for each of the "mini" wallets, call
**getBalance** to get its balance, format it with
**ethers.utils.formatEther(balance).** Create a div, append the address,
its balanc and create the qrcode.

![](/assets/exercises-client-side-wallets-ethersjs-011.png)

Go to **\[View Addresses\]**, type password and click **\[Show
Addresses\]**. Due to asynchronous, addresses might be mixed.

![](/assets/exercises-client-side-wallets-ethersjs-013.png)

Send Transactions
-----------------

Here we will implement the **\[Send Transaction\]** section. We will
create the functionality to sign and send transactions on the Ropsten
Ethereum Network. After a provided password we will decrypt the json in
the local storage, derive first 5 private keys and load the in the
memory of the program. After that, a form will appear with the sender
address, from address and value to send. The sender address will be
chosen from a dropdown of the five derived. First, we will sign the
transaction and then broadcast it to the network.

Go to **unlockWalletAndDeriveAddresses** method in wallet.js. This
method will decrypt the local storage json, load 5 "mini" wallets in the
memory of the program and fill the UI. **Decrypt** the wallet and with
the callback result derive the "mini" wallets, save them in **wallets
object variable**, and append each of the addresses to the select
element as an option. Then show the div with the form.

![](/assets/exercises-client-side-wallets-ethersjs-014.png)

**renderAddresses** can again be implemented inside
**unlockWalletAndDeriveAddresses.**

![](/assets/exercises-client-side-wallets-ethersjs-016.png)

Now implement **signTransaction** method. It will take one of the
addresses from the dropdown, recipient address, value of ETH and sign
it. Take the sender wallet, build a transaction, and sign it and append
to the textarea the signature:

![](/assets/exercises-client-side-wallets-ethersjs-018.png)

Then create **sendSignedTransaction** method which will take the signed
transaction hash from the textarea. The provider will take it and call
**sendTransaction(signedTransaction)**. With the return hash as
callback, show it as a message and in the
**\#textareaSendTransactionResult** show URL to Etherscan:

  ----------------------------------------
  https://ropsten.etherscan.io/tx/{hash}
  ----------------------------------------

![](/assets/exercises-client-side-wallets-ethersjs-021.png)

Export JSON to file
-------------------

Create a section and methods needed to export the JSON in the local
storage to a file.

(Optional) Read from a Contract
-------------------------------

Create a section and read methods of contract of your own (e.g.
ArrayOfFacts.sol contract from the previous exercises).

(Optional) Write to a Contract
------------------------------

Create a section that writes data to a contract of your own (e.g.
ArrayOfFacts). Enter a password, decrypt the HD Wallet from the local
storage JSON, show the first five addresses, select an address and enter
a new fact.

What to Submit?
===============

Create a **zip file** (e.g. **username-client-side-wallet.zip**) holding
the whole wallet implementation (libraries, html, css & javascript
files).

Submit your **zip** file as **homework** at the course Website.
