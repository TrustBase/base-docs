---
id: trustbase-network
title: Connect TrustBase testnet
sidebar_label: Connect TrustBase testnet
---

## TrustBase testnet

At the present trustbase client supports network for `local` and `testnet`

### Connect to trustbase testnet

Connect to the trustbase testnet, running:

```
./target/release/trustbase
```

Use the --help flag to find out which flags you can use when running the node.

### Setup trustbase fullnode

If you want to connect the node remotely, run

```
./target/release/trustbase --ws-external --rpc-cors all
```

Upon the command, the client start to sync with trustbase testnet, it may take a while.


## Running an Archive Node

To keep the full state with trustbase network, use the --pruning flag:

```
./target/release/trustbase --pruning archive
```

## Connect to PolkaJS UI

Connect ot  [PolkaJS UI] (https://polkadot.js.org/apps), Open your web browser, navigate to
https://polkadot.js.org/apps/#/settings?rpc=ws://127.0.0.1:9945
The link provided above includes the rpc URL parameter, which instructs the Apps UI to
connect to the URL that was provided as your local node.To manually configure Apps
UI to connect to another node:

Click on the top left network icon and set the custom endpoint is set to ws://127.0.0.1:9945.