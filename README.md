# NEAR CLI

near CLI is your **human-friendly** companion that helps to interact with [NEAR Protocol](https://near.org) from command line.

Just run `near` and let it guide you through!

<p>
  <img src="docs/media/create-account.svg" alt="" width="1200">
</p>

## Install

You can find binary releases of `near` CLI for your OS on the [Releases page](https://github.com/near/near-cli-rs/releases/).

### Install prebuilt binaries via shell script (macOS, Linux, WSL)

```sh
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/near/near-cli-rs/releases/latest/download/near-cli-rs-installer.sh | sh
```

### Install prebuilt binaries via powershell script (Windows)

```sh
irm https://github.com/near/near-cli-rs/releases/latest/download/near-cli-rs-installer.ps1 | iex
```

### Run prebuilt binaries with npx (Node.js)

```sh
npx near-cli-rs
```

### Install prebuilt binaries into your npm project (Node.js)

```sh
npm install near-cli-rs
```

### Install from source code (Cargo)

Install it with `cargo`, just make sure you have [Rust](https://rustup.rs) installed on your computer.

```bash
cargo install near-cli-rs
```

or, install the most recent version from git repository:

```bash
$ cargo install --git https://github.com/near/near-cli-rs
```

### Install on CI (GitHub Actions)

It is often desirable to use `near` CLI from CI to automate some actions, so here is an example of how you can make a function call during CI:

```yml
name: Release
on:
  push:
    branches: [main]

jobs:
  deploy-widgets:
    runs-on: ubuntu-latest
    name: Make a function call on mainnet
    env:
      NEAR_NETWORK_CONNECTION: mainnet
      NEAR_CONTRACT_ACCOUNT_ID: ${{ vars.NEAR_CONTRACT_ACCOUNT_ID }}
      NEAR_SIGNER_ACCOUNT_ID: ${{ vars.NEAR_SIGNER_ACCOUNT_ID }}
      NEAR_SIGNER_ACCOUNT_PUBLIC_KEY: ${{ vars.NEAR_SIGNER_ACCOUNT_PUBLIC_KEY }}
      NEAR_SIGNER_ACCOUNT_PRIVATE_KEY: ${{ secrets.NEAR_SIGNER_ACCOUNT_PRIVATE_KEY }}

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Install near CLI
      run: |
        curl --proto '=https' --tlsv1.2 -LsSf https://github.com/near/near-cli-rs/releases/download/v0.7.4/near-cli-rs-installer.sh | sh

    - name: Call some function
      run: |
        near contract call-function as-transaction "$NEAR_CONTRACT_ACCOUNT_ID" 'function_name_here' json-args '{}' prepaid-gas '100 TeraGas' attached-deposit '0 NEAR' sign-as "$NEAR_SIGNER_ACCOUNT_ID" network-config "$NEAR_NETWORK_CONNECTION" sign-with-plaintext-private-key --signer-public-key "$NEAR_SIGNER_ACCOUNT_PUBLIC_KEY" --signer-private-key "$NEAR_SIGNER_ACCOUNT_PRIVATE_KEY" send
```

You will need to configure GitHub Actions Secrets and Variables and once it is ready, this CI will only take a couple of _seconds_ to complete!

See how it is used in [near/devgigsboard](https://github.com/near/devgigsboard).

## Run

Once installed, you just run it with `near` command:

```bash
$ near

? What are you up to? (select one of the options with the up-down arrows on your keyboard and press Enter)
> account     - Manage accounts
  tokens      - Manage token assets such as NEAR, FT, NFT
  staking     - Manage staking: view, add and withdraw stake
  contract    - Manage smart-contracts: deploy code, call functions
  transaction - Operate transactions
  config      - Manage connections in a configuration file (config.toml)
  extension   - Manage near CLI and extensions
[↑↓ to move, enter to select, type to filter]
```

The CLI interactively guides you through some pretty complex topics, helping you make informed decisions along the way.

## [Read more in English](docs/README.en.md)  
  - [Usage](docs/README.en.md#usage)
  - [Installation](docs/README.en.md#installation)
  - [User Guide](docs/README.en.md#user-guide)
  - [Config](docs/README.en.md#config)
  - [Building](docs/README.en.md#building)

## [Больше информации на русском языке (in Russian)](docs/README.ru.md)
  - [Применение](docs/README.ru.md#применение)
  - [Установка](docs/README.ru.md#установка)
  - [Инструкция](docs/README.ru.md#инструкция)
  - [Конфигурационный файл](docs/README.ru.md#конфигурационный-файл)
  - [Сборка](docs/README.ru.md#сборка)
