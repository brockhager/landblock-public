# How Landblock Works

Landblock uses a three-layer federation architecture and a tiered adoption model that lets registries join at their own pace — from simple proof publication to full cross-registry interoperability.

## The Three-Layer Architecture

1. **Global Directory** (`RegistryDirectory.sol`) — An on-chain registry of registries. Any participant can discover and verify any other registry in the federation.
2. **Federation Protocol** (`Federation.sol`) — Cross-registry verification and cryptographic proof exchange. Registries can verify each other's records without needing to agree on data formats.
3. **Registry Layer** — Each existing registry publishes proofs through the federation, or new registries can use the Landblock **Registry Template** for LADM-compliant record management from day one.

## Conformance Tiers

Registries join Landblock at one of three tiers, progressing as trust and capability grow:

### Tier 1: Mirror Mode
The existing government registry publishes cryptographic proofs of its records to the blockchain. This creates an immutable **audit trail** that prevents "silent" alteration of old records. Only SpatialUnit proofs are required. No cooperation from other registries is needed.

### Tier 2: Verified
Cross-registry verification begins. The registry publishes both SpatialUnit and BAUnit proofs, enabling bilateral verification agreements with other registries in the federation.

### Tier 3: Full
Complete LADM interoperability. All record types (SpatialUnit, BAUnit, RRR, Party) are published. Identity resolution and evidence exchange across registries are fully supported.

## The Commitment Model

At every tier, Landblock follows the **"No Land Data On Chain"** design invariant:

1. **Assertion**: An authority makes a claim about a record (e.g., a registry records a parcel transfer).
2. **Commitment**: The system generates a cryptographic hash (CID) of the record data.
3. **Anchor**: That hash, along with metadata (authority, timestamp, scope), is recorded to the **Polygon PoS** blockchain (~2s finality, near-zero fees).
4. **Verification**: Anyone can confirm the hash matches the original off-chain document, proving the record existed at that time and has not been tampered with.

A Landblock record means: *"This authority, at this timestamp, made this claim about this record, supported by this evidence."* It does **not** mean the claim is legally correct — that determination remains with courts and governments.

## Bitemporal Versioning

Every record carries three time dimensions:
- **Valid time**: When the registry says the event occurred (registry-asserted).
- **System time**: When Landblock recorded it (UTC, protocol-set).
- **Block timestamp**: When Polygon confirmed it on-chain.

Corrections are never deletions — they create new records with a `supersedes` reference to the prior version. The full history is always preserved.

---

Previous: [Core Concepts](02-core-concepts.md)

Next: [Modules and Apps](04-modules-and-apps.md)
