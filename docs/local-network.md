---
id: local-network
title: Local network
sidebar_label: Run local network
---

This section will show how to start a private trustbase network on your local
computer.

## Install trustbase client

You should already have
[trustbase client](https://github.com/TrustBase/trustbase)
compiled on your computer.
If you do not, please refer to [install guide](install.md).

## Start local chain

Before we generate our own keys, and start a truly unique Substrate network, we can
start with a pre-defined network specification called `local` with two
pre-defined (and definitely not private!) keys known as Alice and Bob.

### Start first node with Alice key

Alice (or whomever is playing her) should run these commands from node-template repository root.

> Here we've explicitly shown the `purge-chain` command. In the future we will omit this You should
> purge old chain data any time you're trying to start a new network.

```bash
# Purge any chain data from previous runs
# You will be prompted to type `y`
./target/release/trustbase purge-chain --base-path /tmp/alice --chain local
```

```bash
# Start Alice's node
./target/release/trustbase \
  --base-path /tmp/alice \
  --chain local \
  --alice \
  --port 30333 \
  --ws-port 9945 \
  --rpc-port 9933 \
  --node-key 0000000000000000000000000000000000000000000000000000000000000001 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator
```

You'll notice that no blocks are being produced yet. Blocks will start being produced once another
node joins the network.

### Bob node Joins

Now that Alice's node is up and running, Bob can join the network by bootstrapping from her node.
His command will look very similar.

```bash
./target/release/node-template purge-chain --base-path /tmp/bob --chain local
```

```bash
./target/release/trustbase \
  --base-path /tmp/bob \
  --chain local \
  --bob \
  --port 30334 \
  --ws-port 9946 \
  --rpc-port 9934 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp
```

If all is going well, after a few seconds, the nodes should peer together and start producing
blocks.

Once you've verified that both nodes are running as expected, you can shut them down.

