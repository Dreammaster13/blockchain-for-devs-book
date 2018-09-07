# Decentralized Storage and IPFS

## Decentralized Storage Systems, IPFS, Swarm, Storj, Sia, Filecoin, …

# Table of Contents
- Decentralized Storage
- IPFS
- IPFS Concepts
- IPFS API
- Decentralized Messaging
- Storj
- Sia
![](/assets/decentralized-storage-and-ipfs-table-of-contents-01.png)
![](/assets/decentralized-storage-and-ipfs-table-of-contents-02.png)
![](/assets/decentralized-storage-and-ipfs-table-of-contents-03.png)
![](/assets/decentralized-storage-and-ipfs-table-of-contents-04.png)
![](/assets/decentralized-storage-and-ipfs-table-of-contents-05.png)


# Decentralized storage
- **The internet problems**:
  - Centralization
  - Files can disappear
  - Bandwidth
- **Sharing files across a peer-to-peer network**
  - The files are **encrypted** and only **owner** of the file can unlock it
  - **Backup** on many nodes
  - File is **splitted** in many nodes


# Decentralized Storage

```cs
IPFS and Swarm
```

![](/assets/decentralized-storage-and-ipfs-decentralized-storage-01.png)


# IPFS
- **IPFS** == Inter Planetary File System
  - **D**istributed **H**ash **T**able (**DHT**)
  - Each file is **unique**
  - Remove **duplications**
  - **Routing**
- Decentralized p2p storage system
  - Not related to Ethereum directly 
  - Can be integrated with Ethereum
![](/assets/decentralized-storage-and-ipfs-ipfs-01.png)


# IPFS Concepts
- Each **IPFS node**:
  - **Hosts** own files / folders
  - Helps the other p2p nodes (routes requests)
  - Can **pin** files from other nodes
- If a node goes **down**, its content disappears in **24 hours**
  - Unless **pinned** from someone else
- **No payment**, no tokens, no token economy
  - You host your files and help the others host their files


# Content-Addressable Storage Model
- IPFS uses a **content-addressable** storage model
  - Content is identified by its hash (currently SHA256)
  - If you change the content, its address (hash) will also change!

```cs
some content
```



# Running IPFS and Uploading Data
- Install IPFS – https://dist.ipfs.io/#go-ipfs
- Initialize the local configuration
- Set up Cross Origin Resource Sharing

```cs
ipfs init
```

![](/assets/decentralized-storage-and-ipfs-running-ipfs-and-uploading-data-01.png)


<!-- # Running IPFS and Uploading Data -->
- Run the IPFS daemon
- Adding files to the IPFS

```cs
ipfs daemon
```

![](/assets/decentralized-storage-and-ipfs-running-ipfs-and-uploading-data-2-01.png)
![](/assets/decentralized-storage-and-ipfs-running-ipfs-and-uploading-data-2-02.png)


# IPFS: Accessing the Resources
![](/assets/decentralized-storage-and-ipfs-ipfs-accessing-the-resources-01.png)


# IPFS: Additional commands 
- Manipulate the Swarm, e.g. open a connection
- Objects
- Pin objects to local storage
- Sweep your repository
- Publish IPFS names
- Verify objects in the filestore 


# IPFS: How It Works?
- Nodes hold **content**
  - Identified by **ID**
- Can "**pin**" content from other nodes (by ID)
- Content is **cached** for few hours in each node
- If a node goes down, its content goes unavailable
  - Unless it is pinned by someone
![](/assets/decentralized-storage-and-ipfs-ipfs-how-it-works-01.png)


# IPFS Web UI
- Open the **IPFS Web UI**here: http://localhost:5001/webui
![](/assets/decentralized-storage-and-ipfs-ipfs-web-ui-01.png)


# IPFS: HTTP Gateway
- IPFS resources can be accessed through https://ipfs.io/ipfs/{id} 
![](/assets/decentralized-storage-and-ipfs-ipfs-http-gateway-01.png)


# IPFS Decentralized Messaging

```cs
IPFS pubsub
```

![](/assets/decentralized-storage-and-ipfs-ipfs-decentralized-messaging-01.png)


# IPFS Publish-Subscribe Messaging
- IPFS provides a **p2p messaging**platform (publish-subscribe):
  - https://ipfs.io/blog/25-pubsub/
- Examples:
- IPFS Pub-Sub Room – JavaScript 

```cs
ipfs daemon --enable-pubsub-experiment
```



# Exercise: Publish Files in IPFS
- Using IPFS Client
![](/assets/decentralized-storage-and-ipfs-exercise-publish-files-in-ipfs-01.png)


# IPFS: The JavaScript API – js-ipfs
- Install the "ipfs-api" module
- Creating an instance of "ipfs-api" with ipfs daemon
- In a web browser


# IPFS-api – Files
- Add a file
- Get the content of a file


# Swarm
- Decentralized **content** **storage** 
- Distribution service
- Distributed on computers across the internet
- Run a swarm node to connect to the **Swarm network**
- When you deploy an Ethereum contract on to the blockchain
  - Deployed address 
  - JSON interface of the ABI 
- In the future, the **ABI will be stored on Swarm**
- https://github.com/ethersphere/swarm 
- http://swarm-guide.readthedocs.io/en/latest/introduction.html 
![](/assets/decentralized-storage-and-ipfs-swarm-01.png)


# Storj – Decentralized Storage
- Decentralized and encrypted cloud storage system
- Proof-of-Retrievability
- Uses Kademlia DHT
- Miners and users negotiate contracts over the P2P network
- After an agreement, file is uploaded to miner via HTTP
- Payment over payment channels (similar to LN)
![](/assets/decentralized-storage-and-ipfs-storj-decentralized-storage-01.png)


# Sia
- Decentralized cloud system
- Splits apart files into segments, encrypts and distributes them across P2P network
- File segments are created using **Reed-Solomon erasure coding**
- Uses **Twofish**symmetric cypher
- 1 TB on Sia is around $2 / month
![](/assets/decentralized-storage-and-ipfs-sia-01.png)


# Summary
- Decentralized Storage
- Inter Planetary File System
- IPFS Content-Addressable Storage Model
- IPFS API
- IPFS Decentralized Messaging
- Storj
- Sia
![](/assets/decentralized-storage-and-ipfs-summary-01.png)

# Resources
- Ipfs commands:  **https://ipfs.io/docs/commands/**
- How to host your ipfs files online forever: **https://medium.com/@merunasgrincalaitis/how-to-host-your-ipfs-files-online-forever-f0c56b9b5398**
- Introduction to IPFS :**https://medium.com/@ConsenSys/an-introduction-to-ipfs-9bba4860abd0**




