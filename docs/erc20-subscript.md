---
id: erc20-subscript
title: subscript erc20
sidebar_label: ERC20 contract with subscript
---

This section will show how to build erc20 contract with subscript on trustbase.

## Subscript library

Subscript is a smart contract language written in AssemblyScript for substrate based chain.
It will provide essential substrate api and builtin tools to support contract development.

Subscript is built on top of AssemblyScript and follow all AssemblyScript syntax.
Subscript is more like a development kit with some builtin module and tools.
As assemblyscript is easy to interact with TypeScript and JavaScript,
subscript is much more friendly for DApp developers.

## Collection of subscript library

[subscript/core](https://github.com/ascontract/subscript/tree/master/core) includes
contract library with essential core compoments implemented.
Developers can use the `subscript/core` to interact with the host environment.
It privide basic basic types, storage acceess and contract interface.

## Subscript examples

the [example](https://github.com/ascontract/subscript/tree/master/examples) directory provide some examples to demonstrate how to use the subscript library.
The [Flipper contract](https://github.com/ascontract/subscript/tree/master/examples/flipper) uses low-level api to interact with the contract node and
The [ERC20 contract](https://github.com/ascontract/subscript/tree/master/examples/erc20) demonstrate erc20 with more complex features.