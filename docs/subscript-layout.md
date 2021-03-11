---
id: subscript-layout
title: Layout of subscript contract
sidebar_label: Layout of subscript contract
---

## Using subscript library

Subscript is built on top of AssemblyScript and follow all AssemblyScript syntax.
Subscript is more like a development kit with some builtin module and tools.
As assemblyscript is easy to interact with TypeScript and JavaScript, subscript is much more friendly for DApp developers.

## Demonstration of subscript contract

A simple `counter` contract with subscript.

```
import { storage } from "subscript";
/**
 * External function to increase Counter
 */
@as_external
function increaseCounter(value: i32): void {
  const newCounter = storage.getPrimitive<i32>(0) + value;
  storage.set<i32>(newCounter);
}

/**
 * Readonly funtion to get current Counter
 */
@as_view
function getCounter(): i32 {
  return storage.getPrimitive<i32>(0);
}

```
