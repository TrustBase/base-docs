---
id: contract-wasm
title: Get started with wasm contract
sidebar_label: Introduction to wasm contract
---

## Introduction to wasm smart contract

Trustbase uses Substrate built-in contract pallet to support `wasm smart contract`. `Wasm` is a binary
instruction format for a stack-based virtual machine. Wasm is designed as a portable target for compilation
of high-level languages like C/C++/Rust, enabling deployment on the web for client and server applications.

Smart contract platform allows users to publish additional logic on top of some core blockchain logic.
Since smart contract logic can be published by anyone, including malicious actors and inexperienced developers,
there are a number of intentional **safe guards** built around the smart contract.

- **Fees**: Ensuring that contract developers are charged for the computation and storage they force on the computers running their contract, and not allowed to abuse the block creators.
- **Sandbox**: A contract is not able to modify core blockchain storage or the storage of other contracts directly. It's power is limited to only modifying it's own state, and the ability to make outside calls to other contracts or runtime functions.
- **State Rent**: A contract takes up space on the blockchain, and thus should be charged for simply existing. This ensures that people don't take advantage of "free, unlimited storage".
- **Revert**: A contract can be prone to have situations which lead to logical errors. The expectations of a contract developer are low, so extra overhead is added to support reverting transactions when they fail so no state is updated when things go wrong.

## Storage Rent

A contract deployed to the chain produces a code hash from which new instances of the chain can be created,
but there is currently no rent applied to the code hash itself. The rent applies only to instances of this contract
which have their own contract accounts. Deploying a code hash currently has a one-time byte-fee applied to the transaction,
but no recurring cost.

Storage rent limits the footprint that a contract can have on the blockchain's storage.

An account of a contract instance is charged proportionally to the amount of storage its account uses.
When a contract's balance goes below a defined limit, the contract's account is turned into a "tombstone" (a hash
of the contract's current state) and its storage is cleaned up. A tombstone contract can be restored by
providing the data that was cleaned up when it became a tombstone as well as any additional funds
needed to keep the contract alive. This fee will retroactively apply to missed rent periods.

## Deploy smart contract

Smart contract deployment on Substrate is a little different than on traditional smart contract blockchains.

Whereas a completely new blob of smart contract source code is deployed each time you push a contract on other platforms,
Substrate opts to optimize this behavior. For example, the standard ERC20 token has been deployed to Ethereum thousands of times,
sometimes only with changes to the initial configuration (through the Solidity constructor function).
Each of these instances take up space on the blockchain equivalent to the contract source code size, even though no code was actually changed.

In Substrate, the contract deployment process is split into two halves:

* Putting your code on the blockchain
* Creating an instance of your contract

With this pattern, contract code like the ERC20 standard can be put on the blockchain a single time, but instantiated any number of times. No need to continually upload the same source code over and waste space on the blockchain.

