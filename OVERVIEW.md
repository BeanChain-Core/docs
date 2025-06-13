# BeanChain Overview

**BeanChain** is a modular, transparent blockchain ecosystem built for speed, flexibility, and developer empowerment. Its layered architecture, extensible transaction system, and open node design support both on-chain and off-chain logic — including multi-language smart contracts, Layer 2 tokens, and community-hosted infrastructure.

> Currently in devnet — powered by a growing set of tools, nodes, and SDKs maintained by the **BeanChain Core Team** under **Outlandish Tech**, a division of **Outlandish Creative LLC**.

---

## Core Architecture

BeanChain’s network is built on a layered node system designed for flexibility and scalability:

- **GPN – Genesis Public Node**  
  The root public node. Anchors the network with block history and transaction gossiping.

- **PN – Public Node**  
  Open to external apps and wallets. Hosts public endpoints for submitting transactions and syncing.

- **RN – Reward Node**  
  Issues system-level transactions (faucet, validator rewards, airdrops) and tracks validator trust via ping/pong.

- **CEN – Contract Execution Node** *(in development)*  
  Handles off-chain smart contract logic and submits results as verified Layer 1 or Layer 2 TXs.

- **Historical Node** *(in development)*  
  SQL-based node that stores full block history for use in explorers and external integrations.

> Peripheral nodes like the RN, CEN, and Historical Node are designed to be **customizable**, allowing developers to plug in their own tools or logic while remaining network-compatible.

---

## Key Features

- **Custom Transaction Flags**  
  Native support for TX types like `transfer`, `reward`, `mint`, `contractCall`, `fundedCENCALL`, and more.

- **Off-Chain Execution with CENs**  
  Efficient, scalable contract logic processed outside consensus and verified by nodes.

- **Layer 2 Token Engine**  
  Mint, burn, and transfer custom tokens with balances tracked in a separate Layer2DB.

- **Developer-Built Nodes**  
  The network supports oracles, bots, analytics relays, and more via custom node builds.

- **Multi-Language Contract Support** *(WIP)*  
  Java support is live; Go, Python, and JS are on the roadmap via community SDKs (e.g., `goPack`).

- **Shared SDKs**  
  [`BeanPack-Java`](https://github.com/BeanChain-Core/BeanPack-Java) powers core models, TX validation, cryptographic tools, and serialization logic.

---

## Ecosystem Projects

| Project | Description |
|--------|-------------|
| [`BeanNode`](https://github.com/BeanChain-Core/BeanNode) | Main validator node used for GPN/PN roles |
| [`BeanPack-Java`](https://github.com/BeanChain-Core/BeanPack-Java) | Core SDK shared by all Java-based nodes |
| [`LimaBeanWallet`](https://github.com/BeanChain-Core/LimaBeanWallet) | Wallet interface for managing BEAN and Layer 2 tokens |
| [`BeanChain.io`](https://github.com/BeanChain-Core/BeanChain.io) | Official site for explorer, tools, and validator onboarding |
| [`Reward Node (RN)`](https://github.com/BeanChain-Core/RN) | Handles gas fee rewards, faucet payouts, and early wallet funding |
| *Contract Execution Node (CEN)* | Contract node for off-chain execution (repo coming soon) |
| *Historical Node* | SQL chain archive for explorer/analytics (repo coming soon) |
| [`BaseNode (xNodeTemplate)`](https://github.com/BeanChain-Core/BaseNode) | Lightweight node skeleton for custom apps |

---

## Current Focus

- **Discord is now public** — early members are welcome to join, collaborate, and help shape the community.
- **Historical Node & Explorer** — building out full archival capabilities and explorer tooling.
- **Validator Staking System** — refining trust-based validator selection and on-chain reward distribution.
- **GhostNet** — preparing for a public testnet with validator UX and experimental features.

---

## Get Involved

We're actively building and growing BeanChain. If you're a:

- Developer or protocol engineer  
- Smart contract author or backend dev  
- Artist, designer, or creative contributor  
- Explorer, tester, or community organizer  

…there’s a place for you.

📬 **Reach out:** `team@limabean.xyz`  
💬 **Join the community:** [discord.gg/RMgbSkNF](https://discord.gg/RMgbSkNF)  
🌐 **Visit:** [beanchain.io](https://beanchain.io)
