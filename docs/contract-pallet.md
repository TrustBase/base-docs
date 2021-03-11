---
id: contract-pallet
title: Get started contract runtime
sidebar_label: Contract Runtime
---

## Contract Pallet

Contract pallet extends accounts based on the `Currency` trait to have smart-contract functionality.
It can be used with other modules that implement accounts based on `Currency`.
Smart-contract accounts have the ability to instantiate smart-contracts and make calls to other contract and non-contract accounts.

The smart-contract code is stored once in a `code_cache`, and later retrievable via its `code_hash`.
This means that multiple smart-contracts can be instantiated from the same `code_cache`, without replicating
the code each time.

When a smart-contract is called, its associated code is retrieved via the code hash and gets executed.
This call can alter the storage entries of the smart-contract account, instantiate new smart-contracts,
or call other smart-contracts.

## Contract calls

There are three main call function for contract module.

* `instantiate_with_code` - Deploys a new contract from the supplied wasm binary, optionally transferring
some balance. This instantiates a new smart contract account and calls its contract deploy
handler to initialize the contract.
* `instantiate` - The same as `instantiate_with_code` but instead of uploading new code an
existing `code_hash` is supplied.
* `call` - Makes a call to an account, optionally transferring some balance.

## Gas

Senders must specify a gas limit with every call, as all instructions invoked by the smart-contract require gas.
Unused gas is refunded after the call, regardless of the execution outcome.

If the gas limit is reached, then all calls and state changes (including balance transfers) are only
reverted at the current call's contract level. For example, if contract A calls B and B runs out of gas mid-call,
then all of B's calls are reverted. Assuming correct error handling by contract A, A's other calls and state
changes still persist.

## Failures and Revert

Contract call failures are not always cascading. When failures occur in a sub-call, they do not "bubble up",
and the call will only revert at the specific contract level. For example, if contract A calls contract B, and B
fails, A can decide how to handle that failure, either proceeding or reverting A's changes.
