# Chapter 2.9. Practical Project: DApp Development

## DApp Practical Project: Requirements, Architecture, Wallet, Front-End, Back-End, UI
## 

# Table of Contents
- Project **requirements**
  - **DApp**, based on the Ethereum blockchain
- DApp **architecture**
  - Smart contracts, front-end, wallet, back-end
  - Additional components (e.g. storage, messaging, others)
- DApp **user interface**(UI)
  - Choosing the front-end technologies
  - Prototyping the UI screens for your app
![](/assets/practical-project-building-a-dapp-table-of-contents-01.png)


# DApp: Project Requirements

```cs
UI, Smart Contract, Solidity, Optional Backend
```

![](/assets/practical-project-building-a-dapp-dapp-project-requirements-01.png)


# DApp – Requirements
- Create a **DApp**, based on Ethereum smart contracts
  - Implement the DApp **logic** in **Solidity smart contracts**
  - Hold the DApp **data** in the Ethereum network
    - Use decentralized storage like IPFS
  - Implement the DApp **UI** as **front-end** app (JS / mobile / other)
  - Optionally, use a **back-end** logic (which is centralized)
- Deploy and run the DApp in the **Ropsten** testnet
  - Host the DApp in IPFS + IPNS


# DApp: Project Architecture

```cs
Front-End, Back-End, Wallet Access
```

![](/assets/practical-project-building-a-dapp-dapp-project-architecture-01.png)


# Contracts, Front-End, Wallet, Back-End 
- **Smart contract**logic
  - Decide which functionality will be on-chain and off-chain
- Decide about the **front-end**
  - E.g. simple JS front-end app or based on JS framework (like React)
- Decide on how to access your **wallet**
  - Use the **MetaMask** browser plug-in and the injected Web3 API
  - Use **client-side wallet**, accessed from JS (e.g. from Ethers.js)
  - Use **server-side wallet**, accessed from the server-side API
- Shall you have a **back-end** (a centralized component)?


<!-- # DApp: User Interface ( -->

```cs
Front-End Technologies and UI Prototype
```

![](/assets/practical-project-building-a-dapp-dapp-user-interface-ui-01.png)


# UI Technology for the DApp
- Decide what UI technology to use for the DApp
  - **Vanilla JS**: create a simple UI in pure JavaScript
  - **Mobile app**: Android / iOS / JS mobile framework
  - **React** / **Angular** / **Vue** / other JS front-end framework
  - **Server-side Web app**(ASP.NET MVC / PHP / Django / Node.js)
  - **Desktop app**/ console-based app
  - Other


<!-- # DApp User Interface ( -->
- Prototype the UI of the DApp
  - Home screen
  - View data screens (anonymous access)
  - Register / create wallet screens
  - Login / open wallet screens
  - Sign transaction / edit data screen
  - Other screens (according to pp logic)
  - Logout functionality


# UI Prototype Example: Home Screen
![](/assets/practical-project-building-a-dapp-ui-prototype-example-home-screen-01.png)


# UI Prototype Example: Register Screen
![](/assets/practical-project-building-a-dapp-ui-prototype-example-register-screen-01.png)


# UI Prototype Example: Voting Screen
![](/assets/practical-project-building-a-dapp-ui-prototype-example-voting-screen-01.png)
