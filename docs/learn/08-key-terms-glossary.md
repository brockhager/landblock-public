# Key Terms Glossary

A quick guide to the specialized language of the Landblock Protocol.

## Data Model (LADM)

| Term | Definition |
| :--- | :--- |
| **LADM** | **Land Administration Domain Model** (ISO 19152): The international standard that defines how land information is structured. Landblock's entire data model is built on it. |
| **SpatialUnit** | A unit of land or water. Represented on-chain by a boundary hash, not actual coordinates. Managed by `SpatialUnitRegistry.sol`. |
| **BAUnit** | **Basic Administrative Unit**: The legal grouping that mediates between physical land (SpatialUnit) and legal rights (RRR). You can never link a Party directly to a SpatialUnit. |
| **RRR** | **Rights, Restrictions, and Responsibilities**: What can be done with a BAUnit — ownership, use restrictions, or administrative obligations. Shares must total ≤ 100% + 1bps. |
| **Party** | A person or organization in the system, identified by a DID. |

## Cryptography & Identity

| Term | Definition |
| :--- | :--- |
| **CID** | **Content Identifier**: A unique cryptographic fingerprint of a file (PDF, photo, survey). Only CIDs are stored on-chain; actual files stay off-chain on IPFS/Filecoin. |
| **DID** | **Decentralized Identifier**: A secure, portable digital ID for a person or organization (via SpruceID). Enables selective disclosure without revealing personal data. |
| **Boundary Hash** | A cryptographic representation of land coordinates. Proves the size and shape of a parcel without revealing the location on-chain. |
| **Coords** | Landblock's spatial identity system. L1 URIs are immutable authoritative spatial identifiers; L2 handles are human-readable references. OGC-compliant. |
| **ZKP** | **Zero-Knowledge Proof**: Cryptographic technique that lets you prove something is true without revealing the underlying data. Used by `PrivacyVerifier.sol`. |
| **Tier 1–3 Identity** | **Tier 1**: Self-asserted. **Tier 2**: Community-verified (3 witnesses). **Tier 3**: Authority-verified (government/court — highest legal weight). |

## Protocol & Architecture

| Term | Definition |
| :--- | :--- |
| **Solidity** | The smart contract language used on Polygon PoS (EVM-compatible). Landblock has 21 Solidity contracts secured with OpenZeppelin libraries. |
| **Polygon PoS** | The blockchain Landblock runs on. Provides ~65 TPS, ~2-second finality, and near-zero transaction fees. |
| **Federation** | The network of registries that publish and verify each other's cryptographic proofs. Each registry retains full sovereignty. |
| **Conformance Tier** | How deeply a registry participates: **Mirror** (publish proofs) → **Verified** (cross-registry verification) → **Full** (complete LADM interop). |
| **Mirror Mode** | Tier 1 conformance: A registry publishes cryptographic proofs of its records to create an immutable audit trail, without changing any existing processes. |
| **Commitment-Only Storage** | The binding invariant that the chain stores only hashes, signatures, and event metadata — never full record content. |
| **Protocol Neutrality** | Landblock is a neutral technological backbone. It records attestations; it never decides who owns land or adjudicates disputes. |

## Tokens & Economics

| Term | Definition |
| :--- | :--- |
| **LDBK** | Utility token (21M fixed supply, 8 decimals). Used for fees, staking, and liquidity mining. No governance voting. Deflationary via burns. |
| **LGT** | Governance token (100M initial supply, 18 decimals). Used for DAO proposals, voting, and treasury management. |
| **PropertyToken** | ERC-721 / ERC-1155 tokens representing fractional ownership shares of a BAUnit. |
| **Paymaster** | `LandblockPaymaster.sol` — uses ERC-4337 Account Abstraction to sponsor transaction fees so users don't need cryptocurrency. |

## Governance

| Term | Definition |
| :--- | :--- |
| **Steward** | An independent individual or entity in the Proto-DAO responsible for governing and upgrading the protocol. |
| **Multi-Sig** | A Gnosis Safe wallet on Polygon PoS that requires multiple steward signatures to authorize an action (e.g., a protocol upgrade). |
| **Constitution** | The binding governance document (ratified) that defines what the DAO can and cannot govern. Courts decide truth about land; the DAO decides only how truth is recorded. |
| **Aragon DAO** | The target governance platform. LGT token voting will replace the Multi-Sig for routine governance once the transition is complete. |

---

Previous: [Example Land Transfer Walkthrough](07-example-land-transfer-walkthrough.md)

Next: [Your First Week on Landblock](09-your-first-week-on-landblock.md)
