---
id: contract-transaction
title: Detail of Contract Transaction
sidebar_label: Contract Transaction
---

## Transaction calls

There are three main transaction call for smart contract.

* `instantiate_with_code` - Deploys a new contract from the supplied wasm binary, optionally transferring
some balance. This instantiates a new smart contract account and calls its contract deploy
handler to initialize the contract.
* `instantiate` - The same as `instantiate_with_code` but instead of uploading new code an
existing `code_hash` is supplied.
* `call` - Makes a call to an account, optionally transferring some balance.

## Structure of transactions

### deploy code

Deploying code uses the `instantiate_with_code` which Instantiates a new contract from the supplied `code`
optionally transferring some balance. This is the only function that can deploy new code to the chain.

* `endowment`: The balance to transfer from the `origin` to the newly created contract.
* `gas_limit`: The gas limit enforced when executing the constructor.
* `code`: The contract code to deploy in raw bytes.
* `data`: The input data to pass to the contract constructor.
* `salt`: Used for the address derivation.

### Instantiates a contract

the `instantiate` transaction instantiates a contract from a previously deployed wasm binary.

This function is identical to [`Self::instantiate_with_code`] but without the
code deployment step. Instead, the `code_hash` of an on-chain deployed wasm binary
must be supplied.

### contract call

The `call` transaction makes a call to an account, optionally transferring some balance.

* If the account is a smart-contract account, the associated code will be
executed and any value will be transferred.
* If the account is a regular account, any value will be transferred.
* If no account exists and the call value is not less than `existential_deposit`,
a regular account will be created and any value will be transferred.


## Data of transaction call

### substrate extrinsic

An extrinsic is a piece of information that comes from outside the chain and is included in a block.
Extrinsics fall into three categories: inherents, signed transactions, and unsigned transactions.

Contract call of extrinsic:

[ origin, destination, value,  gas,  calldata]

### contract transaction structure

The contract call data is encoded in the calldata of substrate extrinsic with `SCALE` codec.

The inner contract data of extrinsic:

calldata ⇒ [selector, param1, param2, param3, ...paramN]

selector ⇒ hash(function)



