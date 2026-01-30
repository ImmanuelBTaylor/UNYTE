# UNYTE

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://example.com/build)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://example.com/releases)
[![Discord](https://img.shields.io/discord/1234567890?color=7289da&label=Discord&logo=discord&logoColor=white)](https://discord.gg/unyte)
[![Twitter](https://img.shields.io/twitter/follow/unyte?style=social)](https://twitter.com/unyte)

**UNYTE** is the powerful blockchain server and development runtime at the heart of the **Unyversal Liquidity Exchange (ULE)** ecosystem, developed by **AVIYON**. It serves dual roles as both a **local blockchain node** for zero-cost testing and a **full-featured dev server** for client/server-side rendering, enabling seamless development of decentralized applications (dApps) that integrate frontend, backend, and blockchain layers.

UNYTE bridges traditional web development with blockchain realities: it provides a lightweight, local "fake" private blockchain (running at `localhost:8545`) with pre-funded test accounts, while also powering modern frontend workflows with hot-reloading, framework support (React, Vue, d30.djs), and direct canister interactions. Think of it as Hardhat + Vite + ethers.js --- but native to the ULE stack, optimized for UNYSL canisters, d30.djs scripts, lofi.css styles, and ULE-Protocol liquidity features.

Run UNYTE locally to simulate the entire ULE Network experience without real $ULE gas fees, then deploy to Aviyon Cloud for production P2P hosting.

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [UNYTE in the ULE Stack](#unyte-in-the-ule-stack)
- [UNYTE vs. Other Dev Tools](#unyte-vs-other-dev-tools)
- [Why UNYTE?](#why-unyte)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Examples](#examples)
- [Advanced Usage](#advanced-usage)
- [Development Workflow](#development-workflow)
- [Deployment & Production](#deployment--production)
- [The ULE Ecosystem](#the-ule-ecosystem)
- [Contributing](#contributing)
- [License](#license)

## Overview

UNYTE eliminates the friction of blockchain development by providing:
- **Local Blockchain Node**: A private, isolated ULE-compatible chain with 10 test accounts (each with 100 fake $ULE), zero real gas, instant blocks, and full EVM/ULE compatibility.
- **Frontend Dev Server**: Hot module replacement (HMR), asset serving, and proxying to the local node for wallet connections (e.g., Osmium wallet → `localhost:8545`).
- **Canister Bridge**: UNYTE acts as the runtime glue between frontend code (`.html.uny`, `.djs`) and backend canisters (UNYSL `.uny`), allowing async calls that feel like local function invocations.
- **Framework Agnostic**: Supports modern JS frameworks while natively prioritizing d30.djs and UNYSL embeddings.

Typical local workflow:
1\. Start blockchain: `npx unyte node`
2\. Start dev server: `npm run dev` (or `unyte dev`)
3\. Open `localhost:5173` --- your dApp loads, connects to local chain, deploys/tests canisters instantly.

UNYTE makes ULE development as smooth as Next.js on Vercel, but decentralized by design.

## Key Features

- **Instant Local Chain**: Sub-second blocks, pre-mined $ULE, 10 funded accounts, no syncing/waiting.
- **Wallet Compatibility**: Connect Osmium or any Web3 wallet to `http://localhost:8545` (JSON-RPC).
- **Canister Support**: Deploy and interact with UNYSL actors seamlessly from frontend code.
- **Framework Integration**: Vite-powered dev server with React/Vue/Svelte + d30.djs/lofi.css hot-reloading.
- **Zero Gas Testing**: Simulate transactions, deployments, and liquidity ops without real costs.
- **Cross-Chain Simulation**: Mock ULE-Protocol features (ULPs, instant exits, gas-zaps) locally.
- **Debugging Tools**: Built-in explorer, logs, transaction traces, and canister state inspection.
- **Production Bridge**: Same codebase transitions to Aviyon Cloud nodes with one flag.

## UNYTE in the ULE Stack

UNYTE is the orchestration layer connecting all ULE components:

| Component              | Role with UNYTE                                                                 |
|------------------------|---------------------------------------------------------------------------------|
| **Frontend**           | Serves `.html.uny` / `.djs` / lofi.css with HMR; proxies to local chain.        |
| **Frontend/Backend**   | Bridges d30.djs scripts and UNYSL canisters via simple imports/calls.           |
| **Database/Nodes**     | Connects to Aviyon Cloud P2P nodes; simulates local persistence.                |
| **Blockchain Server**  | **Core**: Runs the local ULE node; handles canister execution and state.        |
| **Infrastructure**     | Integrates ULE-Protocol hooks; enables seamless transition to mainnet.         |
| **Git**                | Aviyon Git compatibility for project versioning.                               |

UNYTE unifies development: one tool for chain simulation, frontend serving, and canister interaction.

## UNYTE vs. Other Dev Tools

| Feature                  | UNYTE (ULE)                  | Hardhat / Foundry            | Ganache                      | Vite + ethers.js             |
|--------------------------|------------------------------|------------------------------|------------------------------|------------------------------|
| **Local Chain**          | ULE-specific + EVM compat    | Ethereum-focused             | Ethereum-only                | Requires separate chain      |
| **Frontend Dev Server**  | Built-in (Vite-like)         | None                         | None                         | Separate (Vite/Create React) |
| **Canister / Actor Model**| Native UNYSL support         | Solidity only                | Solidity only                | Manual integration           |
| **Zero-Gas Testing**     | Yes, full ULE simulation     | Yes (Ethereum)               | Yes                          | Manual setup                 |
| **d30.djs / lofi.css**   | Native embeddings            | None                         | None                         | Custom loaders               |
| **Production Transition**| Aviyon Cloud seamless        | Requires separate deploy     | Local only                   | Manual bridge                |
UNYTE combines the best of dev servers and local chains into one ULE-native tool.

## Why UNYTE?

- **Frictionless Onboarding**: No real money, no waiting, no complex setup --- start building dApps in minutes.
- **Full ULE Fidelity**: Tests everything from UNYSL persistence to ULE-Protocol liquidity pools locally.
- **Developer Experience**: Feels like modern web dev (npm run dev) while handling blockchain "weirdness" automatically.
- **Cost & Speed**: Free testing, sub-second feedback loops, instant deployments.
- **Scalability Path**: Local → Aviyon Cloud → ULE mainnet with minimal changes.

## Installation

1\. **Via ULE Stack Installer**: Download from [ULE.dev](https://ule.dev) --- includes UNYTE.
2\. **NPM (Recommended)**:

   ```

   npm install -g unyte

   unyte --version

   ```

3\. **In Project**:

   ```

   npm install unyte --save-dev

   ```

## Getting Started

1\. Initialize project:

   ```

   npx unyte init my-dapp

   cd my-dapp

   ```

2\. Start local blockchain node (Terminal A):

   ```

   npx unyte node

   ```

   → Spins up `http://localhost:8545` with test accounts.

3\. Start dev server (Terminal B):

   ```

   npm run dev

   ```

   → Opens `http://localhost:5173` (or custom port).

4\. Connect wallet: In browser, add network `http://localhost:8545`, chain ID (default: 1337 or ULE test), import one of the test private keys shown in node logs.

## Examples

### Basic dApp Structure (package.json scripts)

```json

{
  "scripts": {
    "node": "unyte node",
    "dev": "unyte dev",
    "build": "unyte build",
    "deploy": "unyte deploy --network local"
  }
}

```

### Frontend Canister Call (in .djs or React component)

```javascript

// src/components/Counter.jsx (or .djs)
import { useEffect, useState } from 'react';
import { Counter } from '@unyte/canisters'; // UNYTE auto-generates client

export default function Counter() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    Counter.getCount().then(setCount);
  }, []);

  const increment = async () => {
    const newCount = await Counter.increment();
    setCount(newCount);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

```

UNYTE handles provider, signer, and ABI bridging automatically.

## Advanced Usage

- **Custom Chain Config**:

  ```

  npx unyte node --chain-id 4242 --accounts 20 --balance 1000000

  ```

- **Canister Deployment**:

  ```

  unyte deploy counter.uny --name Counter

  ```

- **Mock ULE-Protocol**:

  ```javascript

  import { mockLiquidityPool } from 'unyte/mocks';
  await mockLiquidityPool.deposit('NFT_ID', 1000);

  ```

- **Debug Mode**:

  ```

  npx unyte node --verbose --explorer

  ```

  Opens local block explorer at `localhost:3000`.

## Development Workflow

- **Daily Dev**: `unyte node` + `npm run dev`
- **Testing**: Write scripts/tests that call canisters via UNYTE client
- **Debugging**: Use browser console + node logs + built-in traces
- **Oxygen Studio**: Visual interface for canister interaction and style previews
- **CLI Power**: `unyte` commands for deploy, call, inspect, etc.

## Deployment & Production

1\. Build static assets:

   ```

   npm run build

   ```

2\. Deploy to Aviyon Cloud:

   ```

   unyte deploy --cloud aviyon

   ```

   → Uploads assets to asset canister, logic to logic canister, auto-registers with ULE-Protocol.

3\. Mainnet: Switch provider to real ULE RPC, use real wallet.

## The ULE Ecosystem

UNYTE connects directly to:

- **ULE Network** --- Simulates Layer 1 with $ULE gas.
- **ULE-Protocol** --- Mocks ULPs, instant exits, cross-chain routing.
- **Unyversal SDK** --- Powers gas-zaps and multichain logic.
- **Aviyon Cloud** --- Production P2P hosting and node orchestration.
- **UNYSL / d30.djs / lofi.css** --- Native runtime support.

## Contributing

We welcome issues, PRs, and ideas! Join [Discord](https://discord.gg/unyte). See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT License - see [LICENSE](LICENSE).
