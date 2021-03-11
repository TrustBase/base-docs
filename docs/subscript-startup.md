---
id: subscript-startup
title: Get started with subscript
sidebar_label: Get started with subscript
---

## Get started with subscript library

Subscript is a smart contract language written in AssemblyScript for substrate based chain.
It will provide essential substrate api and builtin tools to support contract development.

Subscript is built on top of AssemblyScript and follow all AssemblyScript syntax.
Subscript is more like a development kit with some builtin module and tools.
As assemblyscript is easy to interact with TypeScript and JavaScript,
subscript is much more friendly for DApp developers.

## How subscript Works

Substrate's Framework for Runtime Aggregation of Modularised Entities (FRAME) contains the contracts pallet,
which implements an API for typical functions smart contracts need (storage, querying information about account, …).

The contracts pallet requires smart contracts to be uploaded to the blockchain as a Wasm blob.

Subscript is a smart contract language which targets the API exposed by contracts. subscript smart contracts are compiled to Wasm.

## Collection of subscript library

[subscript/core](https://github.com/ascontract/subscript/tree/master/core) includes
contract library with essential core compoments implemented.
Developers can use the `subscript/core` to interact with the host environment.
It privide basic basic types, storage acceess and contract interface.