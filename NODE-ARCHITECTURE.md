# BeanChain Node Architecture

This document outlines the various node types and supporting infrastructure maintained and developed by the BeanChain core team. It includes standard node roles, specialized systems, and foundational frameworks that developers can use to extend the network.

---

## Core Node: `BeanNode`  
**Status:** ✅ Complete

The `BeanNode` is the main full node implementation. It supports:

- Block creation and validation
- Transaction processing and state transitions
- Peer-to-peer networking and gossiping
- Modular LevelDB-based storage for blocks, mempool, state, and rejected TXs

### Role-Based BeanNode Instances

#### 1. Genesis Public Node (GPN)  
**Status:** ✅ Complete  
- Primary network bootstrap peer  
- Public API via Spring Boot  
- Handles TX/block gossiping and public mempool access  

#### 2. Public Node (PN)  
**Status:** ✅ Complete  
- Public-facing node for apps and devs  
- Mirrors GPN’s state  
- Offers public API, but not used for bootstrapping  

#### 3. Private Node (PRN)  
**Status:** ✅ Complete  
- Headless, non-API node  
- Outgoing-only sync, ideal for internal validation and development  
- No Spring Boot overhead  

---

## Specialized Node Systems

### 4. Reward Node (RN)  
**Status:** ✅ Complete (CEN-dependent upgrades pending)  
- Runs as a headless Spring Boot service  
- Handles:
  - Faucet payouts
  - Early wallet airdrops
  - Gas fee rewards for validators  
- Currently uses a basic reward logic system  
- Will later implement:
  - Trust score-based ping list (waiting on CEN + frontend validator registry)  
  - Deeper validator trust mechanics post-CEN completion

### 5. Contract Execution Node (CEN)  
**Status:** 🛠️ In Development  
- Processes off-chain smart contracts  
- Accepts:
  - `CENCALL` — contract logic execution
  - `fundedCENCALL` — includes embedded transactions for chain interaction  
- Outputs valid Layer 1 TXs (`TX`, `MintTX`, `CENTX`, etc.)  
- Will be the final step in completing:
  - Validator trust scoring  
  - Distributed contract execution  
  - Project-side contract nodes

### 6. Snapshot Handler Node (SHN)  
**Status:** 🧪 Planned  
- A utility wrapper that automates:
  - Node startup → Sync → Graceful shutdown → Data snapshot → Restart  
- Provides zipped, trusted `data/` snapshots for new nodes  
- Will support fast chain onboarding without syncing from block 0  

### 7. Historical Node (HN)  
**Status:** 🛠️ In Development  
- Maintains a SQL copy of confirmed chain data  
- Powers:
  - Block explorer  
  - Transaction history queries  
  - Token and contract analytics  
- Will ship with a skeleton project for indexing/search layer expansion  

---

## Developer Frameworks

### 8. BaseNode / XNode Framework  
**Status:** ✅ Complete (Validator logic pending CEN/ghostnet)  
- Lightweight modular Java node skeleton  
- Includes:
  - Core P2P messaging  
  - TX processing (Layer 1 and 2)  
  - Minting and burning support  
- Currently uses a **centralized dev-only block builder**  
- Finalization of validator protocols and decentralized block production will occur during **GhostNet test phase**

BaseNode branches will support:
- Event bots  
- Watcher services  
- Custom token nodes  
- Governance oracles  
- Minimalist indexers

---

## Supporting Tools and Deployment

### 9. Box Box  
**Status:** 🧪 Planned  
- Raspberry Pi or USB-bootable preconfigured node  
- GUI or CLI interface for non-technical users  
- Intended to support grassroots decentralization  

### 10. DevSuite  
**Status:** 🛠️ Active & Expanding  
- Internal tooling suite for:
  - Peer connection testing  
  - TX and block simulation  
  - Visual node syncing analysis  
  - Contract/testnet debugging  
- New tools and panels are added as the network infrastructure grows

---

## Summary

BeanChain’s modular node architecture is designed for scalability and clarity. With the core `BeanNode` and peripheral systems like the `RN`, `CEN`, and `HN`, developers can contribute to every layer of the network — from consensus to data indexing and contract execution.  

The BaseNode framework enables rapid development of custom infrastructure, while future systems like the Snapshot Handler and Box Box aim to make decentralized participation more accessible.

The final validator logic and trust-based block production model will be stress-tested during the upcoming **GhostNet** phase, completing the full decentralization loop.

