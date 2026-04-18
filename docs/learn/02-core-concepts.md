# Core Concepts

Before looking at architecture, it's important to understand the building blocks of the Landblock Protocol. Landblock follows the **ISO 19152 Land Administration Domain Model (LADM)**, the international standard for structuring land information.

## The LADM Data Model

The canonical traversal path in Landblock is:

> **SpatialUnit → BAUnit → RRR → Party**

### 1. SpatialUnit (The Where)
A SpatialUnit represents a unit of land or water. Landblock does not store actual coordinates on-chain. Instead, we store a **Boundary Hash** — a cryptographic fingerprint of the geometry that proves its integrity without exposing its location. Spatial identity is managed through the **Coords** system: L1 immutable coordinate URIs serve as authoritative spatial identifiers, with L2 handles for human-readable references.

### 2. BAUnit (The What)
A Basic Administrative Unit (BAUnit) represents the legal or administrative grouping of one or more SpatialUnits. It is the mediator between physical space and legal rights — you can never go directly from a SpatialUnit to a Party. The BAUnit enforces this separation.

### 3. RRR (The Rights)
Rights, Restrictions, and Responsibilities (RRR) describe what can be done with a BAUnit. These include ownership rights, use restrictions, and administrative responsibilities. Share totals on a BAUnit can never exceed 100% (plus 1 basis point tolerance). RRRs are managed by `RRRRegistry.sol`.

### 4. Party (The Who)
A Party represents a person or organization. Landblock uses **Decentralized Identifiers (DIDs)** via SpruceID to manage identities. This allows users to prove things about themselves (like having a government-verified ID) without revealing their personal data on the ledger. Identity tiers:
- **Tier 1**: Self-asserted
- **Tier 2**: Community-verified (3 witnesses)
- **Tier 3**: Authority-verified (government/court — highest legal weight)

### 5. Evidence (The Proof)
Evidence is supporting material — like a deed PDF, a survey, or a witness signature. We convert evidence into **CIDs** (Content Identifiers) via IPFS/Filecoin. The protocol only "anchors" these CIDs on-chain; the actual files stay in secure off-chain storage managed by `EvidenceStore.sol`.

### 6. Dispute (The Status)
When two parties claim overlapping SpatialUnits, a **Dispute Record** is opened on-chain. This transparency prevents fraudulent transfers while the conflict is resolved by the appropriate local authority (court or government). The protocol marks disputes — it never adjudicates them.

### 7. Federation (The Network)
Landblock is a federation of registries. Each registry retains full sovereignty and publishes cryptographic proofs that other registries can verify. No registry can override another. Contested territories across jurisdictions are marked as disputed, never politically adjudicated by the protocol.

---

Previous: [What Is Landblock?](01-what-is-landblock.md)

Next: [How Landblock Works](03-how-landblock-works.md)
