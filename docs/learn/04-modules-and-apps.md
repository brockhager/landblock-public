# Modules and Apps

This page maps the protocol's smart contracts (L1) and front-end applications (L4).

## Core Protocol Contracts (L1 — Solidity on Polygon PoS)

Landblock has 21 Solidity contracts organized by the LADM data model:

### LADM Core Registries
| Contract | Purpose |
| :--- | :--- |
| `SpatialUnitRegistry.sol` | Records spatial units (parcels) as boundary hashes with Coords URIs. |
| `BAUnitRegistry.sol` | Manages Basic Administrative Units — the legal grouping that mediates between land and rights. |
| `RRRRegistry.sol` | Rights, Restrictions, and Responsibilities attached to BAUnits. Enforces share ≤ 100% + 1bps. |
| `IdentityRegistry.sol` | SpruceID DID management with Tier 1–3 identity attestations and cross-registry resolution. |
| `EvidenceStore.sol` | Registry of CIDs linking records to off-chain documents (deeds, surveys, photos). |

### Federation & Directory
| Contract | Purpose |
| :--- | :--- |
| `RegistryDirectory.sol` | On-chain registry of registries — the Global Directory for federation discovery. |
| `Federation.sol` | Cross-registry proof exchange and verification protocol. |
| `CoordsValidator.sol` | Validates L1 coordinate URI format for spatial identity (CC0 spec, OGC compliant). |

### Governance & Tokens
| Contract | Purpose |
| :--- | :--- |
| `LandblockGovernance.sol` | Protocol governance: proposals, voting, and administrative controls. |
| `LDBKToken.sol` | LDBK utility token (21M fixed supply, 8 decimals). Used for fees, staking, liquidity. No governance voting. |
| `LGTToken.sol` | LGT governance token (100M initial supply, 18 decimals). Used for DAO proposals, voting, and treasury. |
| `PropertyToken.sol` | ERC-721 / ERC-1155 for fractional ownership shares of BAUnits. |

### Operations
| Contract | Purpose |
| :--- | :--- |
| `DisputeRecord.sol` | Lifecycle management for overlapping claims and authority rulings. |
| `LandblockPaymaster.sol` | ERC-4337 Account Abstraction paymaster — sponsors gas so users don't need cryptocurrency. |
| `PrivacyVerifier.sol` | ZKP-based selective disclosure for identity and record verification. |

Plus interface contracts (`ISpatialUnitRegistry`, `IBAUnitRegistry`, `IRRRRegistry`, `IRegistryDirectory`, `IPausable`) and `DummyAdminSurface.sol` for testing.

## Front-End Applications (L4)

### 1. Landblock Register (Mobile)
- **Tech**: React Native / Expo
- **Purpose**: Field application for recording GPS, community evidence, and offline forms. Offline-first with sync.

### 2. Landblock Explorer (Web)
- **Tech**: Next.js / Mapbox
- **Purpose**: Public-facing web map for searching, checking audit histories, and reviewing records.

### 3. Landblock Investor (Web)
- **Tech**: Next.js
- **Purpose**: KYC-gated portal for fractional ownership and property token management.

### 4. Privacy Verifier (Web)
- **Tech**: Next.js with ZKP
- **Purpose**: Verify identity and record claims using zero-knowledge proofs without revealing underlying data.

## The Connection (L2–L3)

- **L2 (Storage)**: Apps store documents on **IPFS/Filecoin** and get back a CID. Only the CID is anchored on-chain.
- **L3 (Indexing)**: An off-chain indexer reads Solidity contract events from Polygon PoS and builds LADM-aligned read models (spatial_units, ba_units, rrrs, parties, federation_proofs) in PostgreSQL. Apps query the indexer's REST/GraphQL API, not the blockchain directly.

---

Previous: [How Landblock Works](03-how-landblock-works.md)

Next: [Common Questions](05-common-questions.md)
