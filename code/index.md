---
layout: default
title: Code
parent: Documentation
nav_order: 9
has_children: true
permalink: /code/
description: Complete technical map of the Zipvilization code layer, including contracts, indexing, world execution, shared types, observability, visualization and implementation status.
---

# 💻 Code

The Code layer contains the operational and experimental implementation of Zipvilization.

Everything currently present under `code/` belongs to **Phase 0 / Chapter 0**, unless a file explicitly states otherwise.

This page is the complete entry point to the directory.

It provides direct access to every folder and file currently contained in `code/`.

> If something is not present in `code/`, it does not exist operationally.

---

## 🗺️ Directory Structure

```text
code/
├── README.md
├── STATUS.md
├── index.md
│
├── indexer/
│   ├── README.md
│   └── stub.ts
│
├── shared/
│   ├── README.md
│   ├── types.ts
│   └── contracts/
│       ├── README.md
│       └── ISolum.sol
│
├── solumtools/
│   └── README.md
│
├── solumview/
│   ├── README.md
│   ├── stub.ts
│   └── contracts/
│       ├── evolution.contract.v1.ts
│       ├── icon_catalog.contract.v1.ts
│       ├── pipeline.binding.v1.ts
│       ├── render-input.v1.ts
│       ├── tile-dictionary.v1.ts
│       ├── tilemap.contract.v1.ts
│       ├── ui_tokens.contract.v1.ts
│       ├── visual_determinism.contract.v1.ts
│       ├── walletmode.contract.v1.ts
│       └── zoom.contract.v1.ts
│
├── token/
│   └── contract/
│       ├── .gitignore
│       ├── DEPLOYMENT.md
│       ├── README.md
│       ├── TESTING.md
│       ├── foundry.toml
│       ├── src/
│       │   └── Solum.sol
│       └── test/
│           ├── SolumToken.t.sol
│           ├── SolumTokenLaunch.t.sol
│           ├── SolumTokenLaunch2.t.sol
│           └── mocks/
│               ├── MockDexV2Router.sol
│               └── MockPair.sol
│
└── world/
    ├── README.md
    ├── simulator.ts
    └── snapshot.ts
```

---

## 📌 Root Documents

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/README.md)** | Defines the purpose, limits and development philosophy of the Code layer. |
| **[STATUS.md]({{ site.github.repository_url }}/blob/main/code/STATUS.md)** | Describes the current implementation status and Phase 0 scaffolding. |
| **[index.md]({{ site.github.repository_url }}/blob/main/code/index.md)** | Source file for this technical directory map. |

---

## ⛓️ Token Contract

The token contract directory contains the canonical on-chain implementation of Solum and its Foundry test environment.

### Directory

**[Open `code/token/contract/`]({{ site.github.repository_url }}/tree/main/code/token/contract)**

### Documentation and configuration

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/token/contract/README.md)** | Canonical overview of the Solum smart contract and its operational boundaries. |
| **[DEPLOYMENT.md]({{ site.github.repository_url }}/blob/main/code/token/contract/DEPLOYMENT.md)** | Deployment requirements and post-deployment steps. |
| **[TESTING.md]({{ site.github.repository_url }}/blob/main/code/token/contract/TESTING.md)** | Foundry testing strategy and test-suite guidance. |
| **[foundry.toml]({{ site.github.repository_url }}/blob/main/code/token/contract/foundry.toml)** | Foundry project configuration. |
| **[.gitignore]({{ site.github.repository_url }}/blob/main/code/token/contract/.gitignore)** | Files excluded from version control within the contract workspace. |

### Contract source

| File | Purpose |
|------|---------|
| **[Solum.sol]({{ site.github.repository_url }}/blob/main/code/token/contract/src/Solum.sol)** | Canonical Solidity implementation of the Solum token contract. |

### Contract tests

| File | Purpose |
|------|---------|
| **[SolumToken.t.sol]({{ site.github.repository_url }}/blob/main/code/token/contract/test/SolumToken.t.sol)** | Core token behavior tests. |
| **[SolumTokenLaunch.t.sol]({{ site.github.repository_url }}/blob/main/code/token/contract/test/SolumTokenLaunch.t.sol)** | Initial launch behavior tests. |
| **[SolumTokenLaunch2.t.sol]({{ site.github.repository_url }}/blob/main/code/token/contract/test/SolumTokenLaunch2.t.sol)** | Additional launch and integration scenarios. |
| **[MockDexV2Router.sol]({{ site.github.repository_url }}/blob/main/code/token/contract/test/mocks/MockDexV2Router.sol)** | Mock decentralized exchange router used by the test suite. |
| **[MockPair.sol]({{ site.github.repository_url }}/blob/main/code/token/contract/test/mocks/MockPair.sol)** | Mock liquidity pair used by the test suite. |

---

## 📡 Indexer

The indexer layer reads on-chain state and produces deterministic, queryable snapshots.

### Directory

**[Open `code/indexer/`]({{ site.github.repository_url }}/tree/main/code/indexer)**

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/indexer/README.md)** | Defines the responsibility and limits of the indexing layer. |
| **[stub.ts]({{ site.github.repository_url }}/blob/main/code/indexer/stub.ts)** | Initial TypeScript scaffolding for deterministic on-chain ingestion. |

---

## 🌍 World

The World layer contains deterministic world rules, evolution logic and snapshot construction.

### Directory

**[Open `code/world/`]({{ site.github.repository_url }}/tree/main/code/world)**

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/world/README.md)** | Defines the purpose and constraints of the world execution layer. |
| **[simulator.ts]({{ site.github.repository_url }}/blob/main/code/world/simulator.ts)** | Deterministic world simulation scaffolding. |
| **[snapshot.ts]({{ site.github.repository_url }}/blob/main/code/world/snapshot.ts)** | Snapshot structures and deterministic world-state generation. |

---

## 🔍 SolumTools

SolumTools is the observability layer.

It exposes existing on-chain facts without adding interpretation.

### Directory

**[Open `code/solumtools/`]({{ site.github.repository_url }}/tree/main/code/solumtools)**

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/solumtools/README.md)** | Defines the scope, guarantees and boundaries of the observability layer. |

---

## 🎨 SolumView

SolumView contains the deterministic visual contracts used to render world state.

It does not access the blockchain directly and does not redefine world meaning.

### Directory

**[Open `code/solumview/`]({{ site.github.repository_url }}/tree/main/code/solumview)**

### Core files

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/solumview/README.md)** | Defines SolumView and the principles of deterministic rendering. |
| **[stub.ts]({{ site.github.repository_url }}/blob/main/code/solumview/stub.ts)** | Initial implementation scaffolding for the visual layer. |

### Visual contracts

| File | Purpose |
|------|---------|
| **[evolution.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/evolution.contract.v1.ts)** | Defines visual evolution behavior. |
| **[icon_catalog.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/icon_catalog.contract.v1.ts)** | Defines the canonical icon catalogue. |
| **[pipeline.binding.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/pipeline.binding.v1.ts)** | Binds visual contracts to the rendering pipeline. |
| **[render-input.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/render-input.v1.ts)** | Defines the input accepted by the rendering layer. |
| **[tile-dictionary.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/tile-dictionary.v1.ts)** | Defines the canonical tile dictionary. |
| **[tilemap.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/tilemap.contract.v1.ts)** | Defines deterministic tilemap construction. |
| **[ui_tokens.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/ui_tokens.contract.v1.ts)** | Defines shared visual and interface tokens. |
| **[visual_determinism.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/visual_determinism.contract.v1.ts)** | Defines deterministic visual-output requirements. |
| **[walletmode.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/walletmode.contract.v1.ts)** | Defines wallet-oriented rendering behavior. |
| **[zoom.contract.v1.ts]({{ site.github.repository_url }}/blob/main/code/solumview/contracts/zoom.contract.v1.ts)** | Defines zoom levels and zoom-dependent behavior. |

---

## 🧩 Shared

The Shared layer contains types, interfaces and boundary definitions reused across technical layers.

### Directory

**[Open `code/shared/`]({{ site.github.repository_url }}/tree/main/code/shared)**

### Shared files

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/shared/README.md)** | Defines the responsibility and constraints of the shared layer. |
| **[types.ts]({{ site.github.repository_url }}/blob/main/code/shared/types.ts)** | Shared TypeScript types used across the implementation. |

### Shared contract artifacts

**[Open `code/shared/contracts/`]({{ site.github.repository_url }}/tree/main/code/shared/contracts)**

| File | Purpose |
|------|---------|
| **[README.md]({{ site.github.repository_url }}/blob/main/code/shared/contracts/README.md)** | Explains the role of developer-facing contract interfaces and artifacts. |
| **[ISolum.sol]({{ site.github.repository_url }}/blob/main/code/shared/contracts/ISolum.sol)** | Solidity interface used by off-chain or integration components. |

---

## 🔄 Technical Flow

The current implementation can be read in this order:

```text
Solum.sol
   │
   ▼
Indexer
   │
   ▼
World
   │
   ├── SolumTools
   └── SolumView
   │
   ▼
Shared types and interfaces
```

Recommended exploration path:

1. Read **[Code Layer]({{ site.github.repository_url }}/blob/main/code/README.md)**.
2. Check **[Current Status]({{ site.github.repository_url }}/blob/main/code/STATUS.md)**.
3. Inspect the **[Solum contract]({{ site.github.repository_url }}/blob/main/code/token/contract/src/Solum.sol)**.
4. Continue through **[Indexer]({{ site.github.repository_url }}/tree/main/code/indexer)**.
5. Read the **[World layer]({{ site.github.repository_url }}/tree/main/code/world)**.
6. Inspect **[SolumTools]({{ site.github.repository_url }}/tree/main/code/solumtools)** and **[SolumView]({{ site.github.repository_url }}/tree/main/code/solumview)**.
7. Use **[Shared]({{ site.github.repository_url }}/tree/main/code/shared)** to understand common types and interfaces.

---

## ⚠️ Operational Boundary

The presence of a file does not imply that it is deployed, active or canonical.

Some components are scaffolding or experimental stubs.

Operational status must be determined from:

1. the implementation itself;
2. the relevant README;
3. `STATUS.md`;
4. explicit deployment evidence.

Code is necessary, but code alone is not a promise.
