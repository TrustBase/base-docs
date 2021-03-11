---
id: subscript-core
title: Subscript Core lib
sidebar_label: Subscript Core lib
---

## Core library

The subscript core library provide basic interfaces of substrate contract runtime

## Collection of core library

Collection of core library including:

* env - substrate seal api for interacting with contract executor.
* context - The information of the contract execution.
* types - Basic types defined for contract primitive.
* crypto - Hash funtions utils.

## seal api

`core/env` defines all the seal api of substrate [contract runtime interface](https://github.com/paritytech/substrate/blob/master/frame/contracts/src/wasm/runtime.rs).

`seal api` are low-level interface of substrate host functions.

## context

`core/context` defines the contract informations of execution context.

The context interfaces:

* blockNumber
* timestamp
* input
* caller
* address


## crypto

`core/crypto` provide hash functions utils to make digest of raw input.

There are four builtin hash functions:

* blake2b128: BLAKE2 128-bit hash
* blake2b256: BLAKE2 256-bit hash
* keccack256: KECCAK 256-bit hash(used in Ethereum), not the same with sha3
* sha256: SHA2 256-bit hash

## types

`core/types` includes basic builtin types such as `balance`, `AccountId`, `Address`