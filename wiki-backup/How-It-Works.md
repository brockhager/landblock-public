# How It Works

Landblock enables land registries to publish cryptographic proofs of their records, creating a verifiable audit trail without storing sensitive data on-chain. This "Mirror Mode" approach lets registries join incrementally, starting with read-only proofs and progressing to full cross-registry interoperability.

## The Cryptographic Proof Flow

```
Registry → Landblock → Verifier
```

1. **Registry Issues Proof**: A government registry (e.g., SUNARP in Peru) records a land transaction. It generates a cryptographic hash (CID) of the record and metadata.
2. **Landblock Anchors Proof**: The hash is stored on Polygon PoS as immutable metadata. The actual record stays off-chain in the registry's secure storage.
3. **Verifier Checks Integrity**: Anyone can verify the hash matches the original document, proving the record existed at that time and hasn't been tampered with.

No land coordinates, personal data, or documents are stored on-chain — only opaque hashes that prove integrity.

## Tiered Disclosure Framework

Registries control who sees what:
- **Public**: Metadata visible to all (e.g., parcel exists, last updated).
- **Restricted**: Metadata + gated content (e.g., coordinates visible to authorized parties).
- **Sealed**: Existence only (e.g., confirms a record exists without revealing details).

This respects national privacy laws while enabling selective sharing for lending, inheritance, or dispute resolution.

## Federation Liaison Service

Cross-registry queries use a three-tier routing system:
- **Tier 1: AI-Automated**: Standard queries resolved by AI without human intervention.
- **Tier 2: Facilitated**: Queries requiring review use DID-authenticated messaging between registries, with on-chain outcome recording.
- **Tier 3: Escalated**: Complex disputes involve human operators for final resolution.

## Bitemporal Versioning

Every record has three timestamps:
- **Valid Time**: When the registry says the event occurred (e.g., deed signed in 2020).
- **System Time**: When Landblock recorded it (protocol-set UTC).
- **Block Time**: When Polygon confirmed it on-chain.

This handles retroactive corrections, late evidence, and temporal disputes precisely.

## Example: Alice Sells Land to Bob

1. Alice's registry records ownership, generates proof hash.
2. Hash anchored on Landblock; record stored off-chain.
3. Bob's bank verifies proof via Federation Liaison Service.
4. Transaction completes with cryptographic assurance.

→ Next: [Roadmap](Roadmap.md)