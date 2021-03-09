---
id: setup-ink-dev
title: Setup ink! environment
---

## Using Ink！

A prerequisite for compiling smart contracts is to have Rust and Cargo installed. Here's [an installation guide](https://doc.rust-lang.org/cargo/getting-started/installation.html).

trustbase support WebAssembly smart contracts written with ink!.

This article will walk through the compiling and deployment process for an Ink smart contract.

## Install ink! CLI

You can install the ink! command line utility `cargo-contract`, a tool for helping setting up and managing WebAssembly smart contracts written with ink!:

```
cargo install cargo-contract --vers 0.8.0 --force --locked
```
