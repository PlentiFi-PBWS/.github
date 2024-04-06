# PlentiFi - PBW 2024

Welcome to **PlentiFi** - an all-in-one, non-custodial investment application with seamless web3 UI/UX and native DeFi integration built on [XRPL](https://xrpl.org/docs/) and [XRPL - EVM Sidechain](https://opensource.ripple.com/docs/evm-sidechain/intro-to-evm-sidechain/).

## Introduction 📄

This project was developed as part of the **Paris Blockchain Week Summit 2024 Hackathon**.

PlentiFi is a non custodial platform which aims to onboard people in their investment journey. Wether they want to buy stocks, crypto, raw material or bonds, they will find what they are looking for with us. <br>Web3 is there but you won't see it 👀.

Join us and embark on a journey towards smarter, more accessible investing with **PlentiFi**.   

## Table of Contents

- [PlentiFi - PBW 2024](#plentifi---pbw-2024)
  - [Introduction 📄](#introduction-)
  - [Table of Contents](#table-of-contents)
  - [Features ✨](#features-)
  - [How does it works ?](#how-does-it-works-)
  - [Why is it simple, efficient and secure ?](#why-is-it-simple-efficient-and-secure-)
  - [Getting Started 🚀](#getting-started-)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
  - [Network Information 🔗](#network-information-)
  - [Account Abstraction in PlentiFi](#account-abstraction-in-plentifi)
  - [Account Abstraction setup on the EVM Sidechain 🛠️](#account-abstraction-setup-on-the-evm-sidechain-️)
  - [Account Abstraction setup on the XRPL 🛠️](#account-abstraction-setup-on-the-xrpl-️)
  - [Live contracts addresses 📂](#live-contracts-addresses-)
  - [Team 👥](#team-)


## Features ✨

- **Seamless web3 integration 🔐** : Creating an account takes only 2 steps and signing you transactions has never been easier: thanks to webAuthn technology, you won't have to worry about loosing you private key while their are no trusted third party.
- **All-in-one investment platform 💵** : You can invest in a wide range of assets, from stocks to crypto, raw material or bonds in a few clicks, no need to switch between multiple platforms and pay a ton of fees anymore.
- **Low fees 💲** : We use the more advanced contracts optimizations to provide you with the lowest fees possible, so you can invest more and pay less.
- **Buy, Swap and Sell ↔️** : You can buy, swap and sell your favorite token in a few clicks with extremely low fees.
- **No KYC required 🕵️** : We don't ask for any personal information, you can start investing right away, privately.
- **Advanced recovery system 🛡️** : In case you loose your device, you can recover your account in just a few steps


> Since there is no bundler and entryPoint on the EVM SideChain, we initiated a redeployment of all essential components. This strategic approach was taken to guarantee a user experience on par with that of other blockchains equipped with bundlers and entryPoint (see [Account Abstraction setup]() bellow)

## How does it works ?

This project provides the best optimal **UX OPTIMIZATION** with a completely frictionless onboarding of a new user in a single click. It combines the use of an OSS solidity [FCL](https://github.com/rdubois-crypto/FreshCryptoLib) library (secp256R1 best EVM implementation, presented at EthCC) to implement a FIDO/passkeys powered Userop. We combine it with Infinitism [ERC4337](https://github.com/rdubois-crypto/FreshCryptoLib). The implementation of the [WebAuthnAccount.sol](https://github.com/PlentiFi-HW3b/Contracts/blob/main/src/Accounts/WebAuthnAccount.sol) realizes this combination.

## Why is it simple, efficient and secure ?

Passkeys represent a groundbreaking shift in Web2 security, setting the stage to obsolete traditional password management and its associated vulnerabilities through robust ECC authentication, akin to an Externally Owned Account (EoA). This transformative wave is propelled by ERC-4337, whose integration promises to significantly enhance accessibility and inclusivity in web3. Unlike conventional methods where keys may be stored in browsers, passkeys are securely housed within the secure enclave, offering fortified protection against sophisticated cyber threats.

Moreover, passkeys introduce an effective safeguard against phishing by binding themselves to a specific website, namely the dApp's site. This is further reinforced by Solidity verification through FCL, employing EVM-specific formulas. For the purposes of the hackathon, a version omitting precomputations is utilized, with the most gas-efficient verification function requiring only 69K gas. For a deeper dive into the cryptographic underpinnings, refer to [this document](https://eprint.iacr.org/2023/939).

## Getting Started 🚀

### Prerequisites
You need to install: 
- Node.js (all ts script have been devoloped with v20.5.0)
- npm (v10.4.0 works fine)
- [foundry](https://book.getfoundry.sh/)


### Installation

Please, refer to the readme of each repository to run the project:
- The Contracts repository: [PlentiFi-HW3b/Contracts](https://github.com/PlentiFi-HW3b/Contracts/tree/main)
- The Frontend repository: [PlentiFi-HW3b/WebApp](https://github.com/PlentiFi-HW3b/WebApp)
- The Bundler repository: [PlentiFi-HW3b/Bundler](https://github.com/PlentiFi-HW3b/Bundler)
- The Login Service repository: [PlentiFi-HW3b/Login-Service](https://github.com/PlentiFi-HW3b/Login-Service)

> **Note**: To work, the project needs you to setup each of these repositories as specified in their respective README.md files.

## Network Information 🔗
XRPL is a decentralized, open-source blockchain that provides fast, low-cost, and scalable transactions. It is designed to enable real-time, cross-border payments and is used by financial institutions, payment providers, and developers worldwide. XRPL features a unique consensus algorithm called the XRP Ledger Consensus Protocol, which does not rely on mining and is energy-efficient. The XRPL ecosystem includes a variety of tools and services for developers, such as the XRP Ledger Dev Portal, XRP Ledger API, and XRP Ledger Explorer.


The Ethereum Virtual Machine (EVM) compatible XRP Ledger sidechain enhances the XRP Ledger with high-performance capabilities, supporting up to 1000 transactions per second and immediate block finalization. It is fully EVM-compatible, enabling the deployment and interaction with Solidity-based smart contracts. The sidechain uses a Proof of Authority (PoA) consensus mechanism, managed by CometBFT and the cosmos-sdk with the Ethermint module. It is interoperable with the main XRP Ledger through a dedicated bridge, facilitating seamless integration and use of decentralized applications.

- Public testnet RPC: `https://rpc-evm-sidechain.xrpl.org`
- Chain ID: `1440002`
- Currency symbol: `XRP`
- Testnet block Explorer URL: `https://evm-sidechain.xrpl.org`

## Account Abstraction in PlentiFi 

PlentiFi takes advantage of the Account Abstraction feature to provide a clean user experience: **no need to worry about gas fees or managing your private keys**. The Account Abstraction feature allows users to interact with the blockchain without having to pay gas fees. Instead, the dApp pays the fees on behalf of the user. This feature is enabled by the use of a bundler and entryPoint, which are responsible for paying the gas fees on behalf of the user. The bundler is a smart contract that collects gas fees from the dApp and pays them to the network, while the entryPoint is a smart contract that interacts with the bundler to pay the gas fees.


## Account Abstraction setup on the EVM Sidechain 🛠️

**Since there is no bundler and entryPoint on the evm sidechain**, we initiated a redeployment of all essential components. This strategic approach was taken to guarantee a user experience on par with that of other blockchains equipped with bundlers and entryPoint. The following steps were taken to achieve this:

1. **Entry Point**: The entryPoint was modified to remove the dependency on the bundler. Our contracts evolved in way that we didn't actually need it anymore. We kept it so future hackers can use it to setup their own account abstraction mechanism.
2. **Bundler**: We created a simple bundler to broadcast user operations to the network. It can also act as a paymaster for the user. 
3. **Factory Contracts**: The contracts were modified to remove the dependency on the bundler and entryPoint. The contracts were deployed using the Hardhat framework. Anyone could use our [smart account factory contract](https://github.com/PlentiFi-HW3b/Contracts/blob/main/src/Accounts/WebAuthnAccountFactory.sol) as reference to deploy their own smart Account Factory on the EVM Sidechain.


**The process in a nutshell:**
- the user creates an account through the factory contract (sponsored or not by the app)
- the user create and sign its operation
- the operation is sent to the bundler
- the bundler broadcast the operation to the network
- the operation is executed

## Account Abstraction setup on the XRPL 🛠️

**Since there is no smart contracts on the XRPL**, we built a custom account abstraction mechanism to provide a seamless user experience. 
Using the XRP Ledger's multi-signature feature, we created a multiple authentication method to secure the user's account. even if the user loses his device, he can still recover his account in just a few steps. **There is no secrets to store, no private key to manage, just a simple and secure way to access your account**.
One Part of the multiple authentication method is the use of [Webauthn](https://webauthn.io/) to identify the user so the login service can provide an approval along with the user's device.

The multi signature features allow the login to be one of the signers but no matter what, it will never be able to broadcast a transaction without the user's approval. The user can also add more signers to his account, like computer, phone, tablet, etc. 

> Note: In the future, we would be able to use Xahau's smart contract feature to deploy a most advanced version of our account abstraction mechanism in the XRP Ledger

## Live contracts addresses 📂

Here is the listing of all the deployed contracts on the EVM Sidechain devnet: 

- Account abstraction contracts:
  - Entry Point: `0x2A1D89DCc1C264FfDBD216F109b06Bf56bf83531`         deploy tx: [0x713eae4d62b2225db3346c1f410f522dade7b453297310b4b5fb695b3368a46d](https://evm-sidechain.xrpl.org/tx/0x713eae4d62b2225db3346c1f410f522dade7b453297310b4b5fb695b3368a46d)
  - WebAuthn verifier: `0x8554E79514910b8C4ac587137689b5c9bC1be75E`         deploy tx: [0xf6653cc92a1c75acd8c32e41e61ae2e40be936fb17bc0b30df95bb496e969db4](https://evm-sidechain.xrpl.org/tx/)
  - WebAuthn Account Factory: `0xcFDd8eedA8CD120009f7C7495E96dF1F52Fb98aE`         deploy tx: [0x0c24155f5024fac37e3bae507bd84253138bbed1d7f200d0c08e41e96824619f](https://evm-sidechain.xrpl.org/tx/)
- The Automated Marked Maker (AMM) contract used for the demo: (homemade mock)
  - AMM: `0xF0d7935a33b6126115D21Ec49403e4ce378A42Dd`         deploy tx: [0xdb66741ce66b669a0c2ba4c9c3ebe1a5c10e98d6e898277cf6053a49b05175b2](https://evm-sidechain.xrpl.org/tx/)
- Some ERC20 deployed and used for the demo:
  - WBTC: `0xbEeB29483e810290B2610593B30C589672CCE3c8`         deploy tx: [0x67bd536e66d60af02bf229fd1e590dd1685e4fb3b664ed2da5fbda084c926beb](https://evm-sidechain.xrpl.org/tx/0x67bd536e66d60af02bf229fd1e590dd1685e4fb3b664ed2da5fbda084c926beb)
  - USDT: `0xfA41c676566422887f29FD095Fb8E8FdB2396548`         deploy tx: [0x68f933b9af05f9f84689f296e3f9054912858ee0886a21f8d67e856056f8a609](https://evm-sidechain.xrpl.org/tx/0x68f933b9af05f9f84689f296e3f9054912858ee0886a21f8d67e856056f8a609)
  - APPL: `0x26cA8F4556f2ACDd500F255898710E97Da67825d`         deploy tx: [0x6b6553167a263bc4aee985cc33aa5837f49ece6db9e8737e559506423f939400](https://evm-sidechain.xrpl.org/tx/0x6b6553167a263bc4aee985cc33aa5837f49ece6db9e8737e559506423f939400)
  - BRENT: `0xaE2274E71f2570d4ed4af0384B061b29Ce4b3F7a`         deploy tx: [0x8ed0f3d9580cd2d69e0d27b1909a08519fba6d0f59a4ed5cd233ed03ace02df6](https://evm-sidechain.xrpl.org/tx/0x8ed0f3d9580cd2d69e0d27b1909a08519fba6d0f59a4ed5cd233ed03ace02df6)
  - GOLD: `0xECa9ae3DF171f0EEAC0bA530A92cd6Ef48865D19`         deploy tx: [0x4272d6341a520e61c5da4be04cbcdede34c107b963bb33c5883c1b7032f8914c](https://evm-sidechain.xrpl.org/tx/0x4272d6341a520e61c5da4be04cbcdede34c107b963bb33c5883c1b7032f8914c)
  - IMMO: `0x26F31025D1c0A8a6F6Be75885fCD9A8713e911c7`         deploy tx: [0x5c78c1142bab3f986f6a832dc5cf9ffd2fe09118154085d2cb2694fb3d4a8787](https://evm-sidechain.xrpl.org/tx/0x5c78c1142bab3f986f6a832dc5cf9ffd2fe09118154085d2cb2694fb3d4a8787)
  - US BOND: `0x4be29fA49717486b44465eBbeFF4b7103A676BDe`         deploy tx: [0xa0d7e37a20fb181957ea652d546f4f4113e36971d6a2da83ca26b5177bf14dd4](https://evm-sidechain.xrpl.org/tx/0xa0d7e37a20fb181957ea652d546f4f4113e36971d6a2da83ca26b5177bf14dd4)


## Team 👥 

- Elli610, FinTech Engineer - *Cypher Lab co-founder, Member of KRYPTOSPHERE®*
- Axel Cige, Software Engineer - *Project manager at Air France*
- Imed Retibi, Software Engineer - *Front-end developper at Weblib*
  
--- 

Thank you for your interest in **PlentiFi** 🚀
