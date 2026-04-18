# Example Land Transfer Walkthrough

This guide shows how Landblock's apps and contracts work together in a property transaction, following the LADM traversal path: **SpatialUnit → BAUnit → RRR → Party**.

## The Story: Alice Sells 50% to Bob

### 1. Identity Registration (Party)
Alice uses the **Register App** to create her **Tier 1 Identity** (DID) via SpruceID. She uploads a photo of her ID card, which is converted into a **CID** (fingerprint) and anchored on-chain via `EvidenceStore.sol`. Her DID is registered in `IdentityRegistry.sol`.

### 2. Parcel Recording (SpatialUnit)
Alice records her parcel geometry using GPS in the Register App. The app calculates a **Boundary Hash** and generates a **Coords L1 URI** — the immutable spatial identifier. These are registered in `SpatialUnitRegistry.sol`. The actual coordinates stay off-chain.

### 3. Administrative Unit (BAUnit)
A **BAUnit** is created in `BAUnitRegistry.sol` to represent the legal grouping of Alice's SpatialUnit. This is the entity that rights will be attached to — not the SpatialUnit directly.

### 4. Rights Assignment (RRR)
Alice's ownership right is recorded as an RRR in `RRRRegistry.sol`, linking her Party (DID) to her BAUnit with a 100% share.

### 5. Authority Verification
An **Authority Verifier** (e.g., a local NGO surveyor) reviews Alice's evidence in the Explorer App. Once satisfied, they sign a transaction that promotes Alice's identity to **Tier 3 (Verified)** in `IdentityRegistry.sol`. Her evidence CIDs are attested in `EvidenceStore.sol`.

### 6. Discovery (Bob)
Bob uses the **Explorer App** to browse for property. He sees Alice's parcel is **Authority-Verified** (Tier 3). Since coordinates are off-chain, the map shows a generalized area until Bob requests access to view the exact boundary through the privacy-preserving disclosure flow.

### 7. Fractionalization (Transfer)
Instead of selling the whole parcel, Alice decides to sell Bob a **50% share**:
- `PropertyToken.sol` mints 100 fungible shares (ERC-1155) linked to Alice's BAUnit.
- 50 shares are transferred from Alice's DID to Bob's DID.
- `RRRRegistry.sol` is updated: Alice 50%, Bob 50%. The contract enforces that shares never exceed 100% + 1bps.

### 8. Dispute Check
`DisputeRecord.sol` checks for any active overlapping claims on the SpatialUnit. If clear, the transaction finalizes on Polygon PoS (~2s finality). If a dispute exists, the transfer is blocked until the off-chain authority resolves it.

### 9. Settlement
The entire transaction is sponsored by `LandblockPaymaster.sol` via ERC-4337 — neither Alice nor Bob needed to hold cryptocurrency to complete it.

### 10. View Results
- Bob sees his **50% share** in his **Investor App** portfolio.
- Alice sees her remaining 50% in her **Register App**.
- Both records are visible (with appropriate access controls) in the **Explorer App**.
- The full LADM traversal is intact: `SpatialUnit → BAUnit → RRR → Party` for both Alice and Bob.

---

Previous: [Trust, Security, and Governance](06-trust-security-and-governance.md)

Next: [Key Terms Glossary](08-key-terms-glossary.md)
