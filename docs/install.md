---
id: install
title: Setup TrustBase client
sidebar_label: Setup TrustBase client
---

## Prerequisites

the first thing you will need to do is prepare the computer for Rust development - these steps will vary based
on the computer's operating system. Once Rust is configured, you will use its toolchains to interact
with Rust projects; the commands for Rust's toolchains will be the same for all supported,
Unix-based operating systems..

### Rust Environment

This guide uses [`rustup`](https://rustup.rs/) to help manage the Rust toolchain. First install and
configure `rustup`:

```bash
# Install
curl https://sh.rustup.rs -sSf | sh
# Configure
source ~/.cargo/env
```

Configure the Rust toolchain to default to the latest stable version:

```bash
rustup default stable
```

### WebAssembly Compilation

TrustBase uses [WebAssembly](https://webassembly.org/) (Wasm) to produce portable blockchain
runtimes. You will need to configure your Rust compiler to use
[`nightly` builds](https://doc.rust-lang.org/book/appendix-07-nightly-rust.html) to allow you to
compile TrustBase runtime code to the Wasm target.

### Rust Nightly Toolchain

Developers building with TrustBase should use a specific Rust nightly version that is known to be
compatible with the version of TrustBase they are using; this version will vary from project to
project and different projects may use different mechanisms to communicate this version to
developers. The TrustBase Node Template uses
an [init script](https://github.com/TrustBase/trustbase/blob/master/scripts/init.sh)
and
[Makefile](https://github.com/TrustBase/trustbase/blob/master/Makefile)
to specify the Rust nightly version and encapsulate the following steps. Use Rustup to install the
correct nightly:

```bash
rustup install nightly-<yyyy-MM-dd>
```

### Wasm Toolchain

Now, configure the nightly version to work with the Wasm compilation target:

```bash
rustup target add wasm32-unknown-unknown --toolchain nightly-<yyyy-MM-dd>
```

### Specifying Nightly Version

Use the `WASM_BUILD_TOOLCHAIN` environment variable to specify the Rust nightly version a TrustBase
project should use for Wasm compilation:

```bash
WASM_BUILD_TOOLCHAIN=nightly-<yyyy-MM-dd> cargo build --release
```

Note that this only builds _the runtime_ with the specified nightly. The rest of project will be
compiled with the default toolchain, i.e. the latest installed stable toolchain.

## Compiling TrustBase client

Once the prerequisites are installed, you can use Git to clone the TrustBase repo.

1. Clone trustbase.

   ```bash
   	git clone https://github.com/TrustBase/trustbase
   ```

2. Initialize WebAssembly build environment

   ```bash
    ./scripts/init
   ```

3. Compile the client

   ```bash
   cargo build --release
   ```

The time required for the compilation step depends on the hardware you're using.