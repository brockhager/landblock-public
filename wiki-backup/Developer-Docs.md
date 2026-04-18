# Developer Docs

Welcome to the Landblock Developer Documentation. This section provides technical resources for integrating with, building on, or contributing to the Landblock Protocol.

## Getting Started

Landblock is built on **Polygon PoS**, an EVM-compatible blockchain with ~2-second finality and near-zero fees. Smart contracts are written in Solidity with OpenZeppelin libraries and tested via Foundry.

### Key Technologies
- **Blockchain**: Polygon PoS (mainnet checkpointed to Ethereum)
- **Smart Contracts**: Solidity + OpenZeppelin + Foundry
- **Identity**: SpruceID DIDs with ZKP selective disclosure
- **Storage**: IPFS + Filecoin (off-chain, no land data on-chain)
- **Oracle**: Pyth Network for fee pricing
- **Governance**: Aragon on Polygon
- **Indexing**: The Graph (Polygon subgraph)
- **Spatial**: CoordsApp L1 URIs for canonical coordinates

## Core Concepts for Developers

### Federation Architecture
Landblock uses a three-layer federation:
1. **Global Directory** (`RegistryDirectory.sol`): On-chain registry of participating registries.
2. **Federation Protocol** (`Federation.sol`): Cross-registry verification without semantic harmonization.
3. **Registry Layer**: Individual registries publish proofs or use the Landblock Registry Template.

### Conformance Tiers
Registries adopt incrementally:
- **Mirror Mode**: Publish proofs without workflow changes.
- **Verified**: Bilateral verification with other registries.
- **Full Federation**: Complete LADM interoperability.

### Bitemporal Versioning
Every record has three timestamps:
- **Valid Time**: Registry-asserted event time.
- **System Time**: Landblock recording time (UTC).
- **Block Time**: Polygon confirmation time.

## Contract Addresses (Testnet - Amoy)

- **LandblockGovernance**: 0x65FBa64d0E9a443fA4165D7d77252eFDdD637dEb
- **DummyAdminSurface**: 0x15561ca6726c2DBe3631Ef4Fb4ff9730bC80C257

*Mainnet addresses TBD after Phase 7 audit.*

## Integration Guides

- **Registry Integration**: How to publish proofs from existing systems.
- **DApp Development**: Building on Landblock with Web3 libraries.
- **API Reference**: REST/GraphQL endpoints for indexed data.

## Contributing

- **Code Standards**: Solidity style guide, testing requirements.
- **Security**: Audit processes, bug bounty program.
- **Governance**: Proposing protocol changes via Aragon DAO.

→ Next: [Contract Addresses](Contract-Addresses.md) | Back to [Home](../Home.md)