---
id: build-ink-erc20
title: Build ERC20 on TrustBase
---

## ERC20 Contract

There is a library repo for ERC20 Contract

```
git clone https://github.com/TrustBase/trusted-contracts.git
```

ink! ERC20 contracts locates in ./trusted-contracts/contracts/erc20


## Building ERC20 Contract

Run the following command to compile your smart contract:

```
cd ./contracts/erc20
cargo +nightly contract build
```

This special command will turn your ink! project into a Wasm binary, a metadata file (which contains the contract's ABI) and a .contract file which bundles both. This .contract file can be used for deploying your contract to your chain. If all goes well, you should see a target folder which contains these files:

```
target
└── erc20.wasm
└── metadata.json
└── erc20.contract
```

## Deploying Your Contract

Now that we have generated the Wasm binary from our source code , we want to deploy this contract onto Trustbase chain.

Smart contract deployment on Trustbase chain is a little different than on traditional smart contract blockchains.


Whereas a completely new blob of smart contract source code is deployed each time you push a contract on other platforms, Trustbase chain opts to optimize this behavior. For example, the standard ERC20 token has been deployed to Ethereum thousands of times, sometimes only with changes to the initial configuration (through the Solidity constructor function). Each of these instances take up space on the blockchain equivalent to the contract source code size, even though no code was actually changed.

we will deploy the smart contract use the `Polkadot JS Apps`, Go to `Developer` -> `Contracts` page.
In the `Code` tab. If you have not yet deployed a contract onto your node, the Code tab will be the only one available.

![idv](https://github.com/jizer/Document/blob/main/pic/upload.png?raw=true)


+ Ensure the deployment account is set and it will have a sufficient balance for us to deploy, instantiate and test the contract
+ Drag erc20.wasm onto the compiled contract WASM field
+ Optional: Amend the code bundle name value for a more human-friendly name
+ Drag metadata.json onto the contract ABI field
+ Set the maximum gas allowed to 500,000 to ensure that we supply enough gas to process the transaction

Once configured, hit Upload and then confirm once again. The transactions will take place and the contract code will be deployed.

now we can deploy the contract with the following steps.
![idv](https://github.com/jizer/Document/blob/main/pic/deploy.png?raw=true)

+ Set the endowment value to 20,000 to ensure the new contract account is minted with some value. Like Ethereum contracts, Ink contracts are deployed to a separate address with their own unique AccountId and balance.
+ Again, set the maximum gas allowed to 200,000 to ensure that we supply enough gas for the transaction
+ Hit Deploy and confirm to carry out the transaction.

Calling functions from deployed contract.

![idv](https://github.com/jizer/Document/blob/main/pic/message.png?raw=true)

Our final job is now to ensure that functions are working as expected. You will notice that all the pub(external) functions we defined in the contract are now available to call and test within the Token1 contract:

![idv](https://github.com/jizer/Document/blob/main/pic/call.png?raw=true)