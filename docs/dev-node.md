---
id: dev-node
title: Dev Node
sidebar_label: Run in dev mode
---

This section will show how to start trustbase client in develepment mode.

## Install trustbase client

You should already have
[trustbase client](https://github.com/TrustBase/trustbase)
compiled on your computer.
If you do not, please refer to [install guide](install.md).

## Run trustbase client in development mode

We can add `--dev` option to run client in development mode with pre-defined
(and definitely not private!) keys known as `Alice`.
Run the following commands to start your node:

```bash
# Run a temporary node in development mode
./target/release/trustbase --dev --tmp

This command produce block with single autor `Alice`. If the number after
`finalized:` is increasing, the trustbase client is producing new blocks
and reaching consensus about the state they describe!