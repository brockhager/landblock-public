# Coords Integration with Landblock

## Overview

Coords is an external spatial identity platform that provides immutable coordinate URIs (L1) and resolvable handles (L2) for referencing geographic locations. Landblock integrates with Coords as a first-class external dependency for spatial identity, anchoring parcel assertions via cryptographic commitments while maintaining neutrality and auditability.

This document explains the integration architecture, trust model, and implementation details.

## What is Coords?

Coords is a separate, protocol-grade platform consisting of:

- **Spec (CC0)**: Canonical protocol definition and test vectors
- **Core (MIT)**: Reference CLI implementation in Go
- **Cloud (Hosted)**: Resolver service with alias registry and enterprise features

Coords provides:
- **L1 URIs**: Immutable, checksummed coordinate references (e.g., `coords:47.123456,-122.345678,0#checksum`)
- **L2 Handles**: Human-readable aliases that resolve to L1 URIs

Coords is not an "app" within Landblock; it's an independent spatial identity substrate.

## Integration Architecture

### Commitment-Only Storage (ADR-0004 Compliance)

Landblock stores only cryptographic commitments to Coords L1 URIs on-chain:

- **On-Chain**: `bytes32 coordsCommit = keccak256(bytes(coordsUriCanonical))`
- **Off-Chain**: Full canonical URI emitted in events for auditability

This preserves Landblock's "No Land Data On Chain" invariant while enabling verifiable spatial anchoring.

### Key Components

#### Contracts
- **ParcelRegistry.sol**: Stores `coordsCommit` in parcel records, validates URI canonicality and checksum
- **CoordsValidator.sol**: Library for validating Coords L1 URI format and checksum
- **Events**: `ParcelRegistered` emits full URI and commitment for deterministic reconstruction

#### Indexer
- **SpatialIdentity Table**: Stores canonical URIs, handle provenance, and derived geometry
- **Parcel Table**: References `coordsCommit` for spatial anchoring
- **Deterministic Reconstruction**: Recomputes commitments from event logs

#### Apps
- **L1 Primary**: Display canonical URIs as authoritative references
- **L2 Annotations**: Show handles as user-friendly labels (non-authoritative)
- **Resolution**: Apps resolve handles to L1 URIs before on-chain submission

## Trust Model

### L1 URIs (Immutable)
- **Trustless**: Self-verifying via checksum and spec
- **No External Dependency**: Verifiable from chain data alone
- **Perfect for Audits**: Courts can reconstruct and validate without resolvers

### L2 Handles (Resolvable)
- **Resolver-Dependent**: Requires Coords infrastructure (decentralized or hosted)
- **Non-Authoritative**: Used for UX, not protocol truth
- **Provenance Tracked**: Indexer stores resolution metadata without privilege

### Neutrality Boundary
Landblock remains neutral to Coords governance:
- No inheritance of handle policies
- Spatial uniqueness not enforced at protocol level
- Disputes resolved by authorities, not coordinates

## Implementation Details

### Canonical Form Requirements
Coords L1 URIs must be in canonical form per spec:
- Exact scheme/prefix
- Fixed precision and rounding
- Normalized sign/leading zeros
- Strict range enforcement (lat: [-90,90], lng: [-180,180])
- Checksum included and verified

### Commitment Pattern
```solidity
function registerParcel(
    bytes32 parcelId,
    bytes32 coordsCommit,
    string calldata coordsUriCanonical,
    // ... other params
) external {
    require(coordsCommit == keccak256(bytes(coordsUriCanonical)), "COORDS_COMMIT_MISMATCH");
    require(CoordsValidator.validateL1Uri(coordsUriCanonical), "INVALID_URI");
    // Store coordsCommit on-chain
    emit ParcelRegistered(parcelId, coordsCommit, coordsUriCanonical, ...);
}
```

### Event Design
```solidity
event ParcelRegistered(
    bytes32 indexed parcelId,
    bytes32 indexed coordsCommit,
    string coordsUriCanonical,
    uint8 coordsSpecVersion,
    // ... other fields
);
```

### Indexer Schema
```prisma
model SpatialIdentity {
  coordsCommit       String @id
  coordsUri          String
  coordsSpecVersion  Int?
  resolvedFromHandle String?
  resolverId         String?
  resolvedAt         DateTime?
}

model Parcel {
  parcelId     String @id
  coordsCommit String
  coordsUri    String
  // ... other fields
}
```

## Key Decisions

- **ADR-0019**: Spatial Identity via Coords (binding architectural decision)
- **Commitment Storage**: bytes32 hash on-chain, full URI in events
- **L1 Primacy**: Canonical URIs are protocol truth; handles are UX
- **Versioning**: `coordsSpecVersion` in events for future-proofing
- **Multiple Assertions**: Allowed per spatial anchor; uniqueness not enforced

## Validation and Testing

- **Checksum Verification**: Enforced on-chain and off-chain
- **Canonical Enforcement**: Contracts validate syntax; indexer validates semantics
- **Test Vectors**: Use Coords spec test vectors for integration tests
- **Historical Validity**: Stricter rules apply to indexer, not contracts

## References

- [ADR-0019: Spatial Identity via Coords](https://github.com/brockhager/landblock-core/blob/main/docs/05-decisions/ADR-0019-Spatial-Identity-via-Coords.md)
- [ADR-0004: Solidity Contract Layout and Invariants](https://github.com/brockhager/landblock-core/blob/main/docs/05-decisions/ADR-0004-Solidity-Contract-Layout-and-Invariants.md)
- [Coords Protocol Specification](https://coords.example.com/spec) (external)
- [Coords Core Implementation](https://github.com/coords/core) (external)

## FAQ

**Q: Why not store coordinates directly?**
A: Violates "No Land Data On Chain" invariant; commitments provide verifiability without raw data.

**Q: Can handles be authoritative?**
A: No; they resolve to L1 URIs but are non-authoritative for protocol purposes.

**Q: What if Coords changes?**
A: L1 URIs are immutable; versioning in events allows future decoding.

**Q: How are disputes handled?**
A: Spatial conflicts are resolved by authorities; protocol allows multiple claims per location.

This integration ensures Landblock can reference spatial locations securely and neutrally, leveraging Coords as a robust external foundation.