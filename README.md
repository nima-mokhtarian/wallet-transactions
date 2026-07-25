# Wallet Transactions Postman Kit

A Postman collection for pulling wallet transaction history across three
common chain families — EVM (Etherscan-compatible explorers), Bitcoin
(Blockstream Esplora), and Solana (JSON-RPC) — from a single kit.

## Table of Contents
- [Overview](#overview)
- [API Details](#api-details)
- [Getting Started](#getting-started)
- [Available Endpoints](#available-endpoints)
- [Contributing](#contributing)
- [License](#license)
- [Resources](#resources)

## Overview
This repository contains `WalletTransactions.postman_collection.json` and a
companion `WalletTransactions.postman_environment.json`, organized into three
folders — one per chain family — for fetching a wallet's transaction/signature
history without writing any code.

## API Details
- **EVM (Etherscan-compatible)**: `etherscan_base` defaults to
  `https://api.etherscan.io/api`; swap it for `https://api.bscscan.com/api`,
  `https://api.polygonscan.com/api`, etc. to target another Etherscan-family
  explorer. Requires a free `api_key` from the target explorer.
- **Bitcoin (Blockstream Esplora)**: `blockstream_base` defaults to
  `https://blockstream.info/api` — no API key required.
- **Solana (JSON-RPC)**: `solana_rpc` defaults to
  `https://api.mainnet-beta.solana.com` — no API key required for public RPC
  calls at reasonable volume.

No request signing is needed for any of the three — auth (where required) is
a plain query-string API key, resolved automatically from the environment.

## Getting Started
### Prerequisites
- [Postman](https://www.postman.com/downloads/)
- An API key from an Etherscan-family explorer if you plan to use the EVM
  folder (get one from [etherscan.io](https://etherscan.io/apis) or the
  equivalent explorer for your target chain)

### Installation
1. Import both files into Postman:
   - `WalletTransactions.postman_collection.json`
   - `WalletTransactions.postman_environment.json`
2. Select the **Wallet Transactions** environment.
3. Fill in the variables for whichever chain(s) you're using — see
   [Available Endpoints](#available-endpoints) below for which variables each
   folder needs.

## Available Endpoints

### EVM (Etherscan-compatible)
Set `etherscan_base`, `api_key`, `address`, `block_start` (default `0`),
`block_end` (default `99999999`), `page` (default `1`), `offset` (default
`10000`). Covers normal transaction listing (`txlist`).

### Bitcoin (Blockstream Electrs API)
Set `blockstream_base` and `btc_address`. Returns confirmed/unconfirmed
transactions for the address.

### Solana (JSON-RPC)
Set `solana_rpc`, `sol_address`, `sol_limit` (default `1000`), and
optionally `sol_before` (a signature string, for pagination) or `signature`
(to fetch one specific transaction via `getTransaction`).

## Contributing
1. Fork the repository.
2. Create a branch (`git checkout -b feature/your-feature`).
3. Update the collection/environment or README.
4. Open a merge request describing the change and which chain it affects.

## License
MIT — see [LICENSE](LICENSE).

## Resources
- [Etherscan API Docs](https://docs.etherscan.io/)
- [Blockstream Esplora API Docs](https://github.com/Blockstream/esplora/blob/master/API.md)
- [Solana JSON-RPC API Docs](https://solana.com/docs/rpc)
- [Postman Documentation](https://learning.postman.com/docs/getting-started/introduction/)
