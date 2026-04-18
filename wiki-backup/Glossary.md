# Glossary

A comprehensive guide to Landblock terminology. Terms are organized alphabetically with definitions, context, and links to related pages.

## A

**Account Abstraction**: ERC-4337 standard allowing users to pay fees in any token or sponsor transactions. Landblock uses this for gas-free experiences.

**ADR (Architectural Decision Record)**: Documents explaining key design choices. See [How It Works](How-It-Works.md) for examples.

## B

**BAUnit (Basic Administrative Unit)**: Legal grouping of spatial units in LADM. Mediates between physical land and rights. [Core Concepts](02-core-concepts.md)

**Bitemporal Versioning**: Records have valid time (real-world event), system time (protocol recording), and block time (blockchain confirmation).

**Boundary Hash**: Cryptographic fingerprint of land geometry. Stored on-chain for integrity without revealing coordinates.

## C

**CID (Content Identifier)**: IPFS hash of evidence files. Only CIDs are on-chain; files stay off-chain.

**Conformance Tier**: Adoption level — Mirror, Verified, Full Federation. [How It Works](How-It-Works.md)

**Constitution**: Binding governance document defining DAO scope and neutrality. [Constitution](Constitution.md)

**Coords**: Landblock's spatial reference system. L1 URIs are immutable; L2 handles are human-readable.

## D

**DID (Decentralized Identifier)**: Portable digital identity via SpruceID. Enables cross-registry verification.

**Dispute Record**: On-chain marking of overlapping claims. Resolved off-chain by authorities.

## E

**Evidence**: Supporting documents (deeds, surveys) stored on IPFS/Filecoin with CIDs anchored on-chain.

## F

**Federation**: Network of registries sharing proofs. [How It Works](How-It-Works.md)

**Federation Liaison Service**: Three-tier query routing — AI, facilitated, escalated. [How It Works](How-It-Works.md)

**Foundry**: Testing framework for Solidity contracts. Used for invariant testing.

## G

**Gnosis Safe**: Multi-sig wallet for Proto-DAO. [DAO Operations](DAO-Operations.md)

## I

**Identity Tier**: Verification levels — Tier 1 (self-asserted), Tier 2 (community), Tier 3 (authority).

**IPFS/Filecoin**: Decentralized storage for evidence. Content-addressed and permanent.

## L

**LADM (Land Administration Domain Model)**: ISO 19152 international standard for land data. Landblock's foundation.

**LDBK**: Utility token (21M supply). Pays fees; deflationary. [Token Economics](Token-Economics.md)

**LGT**: Governance token (100M supply). DAO voting. [Token Economics](Token-Economics.md)

## M

**Mirror Mode**: Tier 1 adoption — publish proofs without workflow changes. [How It Works](How-It-Works.md)

## N

**Neutrality Lock**: 85% LGT approval + 90-day deliberation for core changes. Protects sovereignty.

## O

**OGC (Open Geospatial Consortium)**: Standards for spatial data. Coords complies with OGC.

## P

**Paymaster**: ERC-4337 contract sponsoring gas fees. [Contract Addresses](Contract-Addresses.md)

**Polygon PoS**: Blockchain platform — EVM-compatible, fast finality, low fees.

**Property Token**: ERC-721/1155 for fractional ownership shares.

**Proto-DAO**: Founding Multi-Sig phase. [DAO Operations](DAO-Operations.md)

**Pyth**: Oracle network for secure price feeds (fee pricing).

## R

**Registry**: Government or authorized institution publishing land records.

**RRR (Rights, Restrictions, Responsibilities)**: Legal relationships between parties and BAUnits. [Core Concepts](02-core-concepts.md)

## S

**Slither**: Static analysis tool for Solidity vulnerabilities.

**Spatial Unit**: Physical land/water area in LADM. [Core Concepts](02-core-concepts.md)

**SpruceID**: DID provider for identity management.

## T

**Tiered Disclosure**: Public/Restricted/Sealed access controls. Registries decide.

## Z

**ZKP (Zero-Knowledge Proof)**: Cryptographic verification without revealing data. Used for privacy.

## Related Resources

- [Key Terms Glossary](08-key-terms-glossary.md) in Learn section
- [API Reference](API-Reference.md) for technical terms
- [FAQ](FAQ.md) for common questions

→ Back to [Home](Home.md)