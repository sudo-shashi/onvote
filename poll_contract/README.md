# Poll Contract

## Overview

This folder contains the Soroban smart contract used by OnVote for storing polls, votes, and poll status on Stellar testnet.

## Main Files

- `src/lib.rs` contains the contract logic
- `Cargo.toml` defines the Rust package and Soroban dependency

## Network Details

- Network: `Stellar Testnet`
- Contract address: `CDPYFRUN6ZRKUIKZR45AMWF7SYPQJL4WRJIBJI2SR3DWRMMANTXXRMD2`
- Contract explorer: https://stellar.expert/explorer/testnet/contract/CDPYFRUN6ZRKUIKZR45AMWF7SYPQJL4WRJIBJI2SR3DWRMMANTXXRMD2
- Sample contract call tx hash: `e5a4df2c3ef97235d1b33ebe043cb66ab5642d53f0319caabc9f98e2239712c8`
- Sample call explorer: https://stellar.expert/explorer/testnet/tx/e5a4df2c3ef97235d1b33ebe043cb66ab5642d53f0319caabc9f98e2239712c8

## Build

From the project root:

```bash
npm run contract:build
```

Or directly with Cargo:

```bash
cargo build --manifest-path poll_contract/Cargo.toml --target wasm32v1-none --release
```

## Deploy

From the project root:

```bash
npm run contract:deploy
```

The deploy script:

- funds a temporary deployer account on testnet when `STELLAR_DEPLOYER_SECRET` is not provided
- uploads the compiled contract WASM
- deploys the contract
- submits a sample `create_poll` contract call
- prints the contract id and transaction hashes as JSON

## Deployment Record

These values were generated on April 27, 2026 during testnet deployment:

- WASM upload tx: `6c6781692a1c69e58231105680b7285f6c77d431fd66645e1df2e55c45a18547`
- Contract deploy tx: `3a83a32bb31421fce9b501b5720f535baf59a52a667eda8b63b16172ae23217c`
- Sample create poll tx: `282d8793c1968e02b32d6d23d688b930a01c316056c908acfd6b685b8089f67e`
