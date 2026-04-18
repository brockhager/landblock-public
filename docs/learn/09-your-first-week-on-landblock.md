# Your First Week on Landblock

Welcome to the Landblock community! Whether you're a citizen, a surveyor, a registry official, or a steward, your first week is about understanding the protocol and establishing your digital presence.

## Day 1: Understanding the Protocol
Read the [Core Concepts](02-core-concepts.md) and understand the LADM data model (`SpatialUnit → BAUnit → RRR → Party`). Remember that Landblock is a verification and federation layer, not a legal authority.

## Day 2: Create Your Identity
Download the **Register App** and create your **Tier 1 (Self-Asserted) DID** via SpruceID. This is your digital identity for everything on the platform. Your DID is registered in `IdentityRegistry.sol` — no cryptocurrency needed thanks to the ERC-4337 Paymaster.

## Day 3: Explore Your Neighborhood
Use the **Explorer App** to see what land in your area is already anchored to the protocol. Check the audit trails for existing SpatialUnits to see how the system handles proof-of-state. Notice how records show attestation tiers (Tier 1/2/3) and temporal history.

## Day 4: Record Your First Witness Attestation
If you're a neighbor, you can act as a **Tier 2 Witness** for someone else's land claim. By signing an attestation, you help your community move toward higher-trust records. Three community witnesses are needed to upgrade a claim from Tier 1 to Tier 2.

## Day 5: Submit Evidence
If you have a formal government deed or survey, submit it as **Evidence** through the Register App. The file is stored on IPFS/Filecoin and a CID is anchored via `EvidenceStore.sol`. In jurisdictions at Tier 2+ conformance, an **Authority Verifier** can then upgrade your identity to **Tier 3 (Verified)**.

## Day 6: Explore Tokenization and Privacy
- Log into the **Investor App** to see how BAUnit shares can be fractionalized using `PropertyToken.sol`.
- Try the **Privacy Verifier** app to see how zero-knowledge proofs let you verify claims without exposing underlying data.

## Day 7: Understand Governance
Read the [Constitution](https://github.com/brockhager/landblock-public/blob/main/CONSTITUTION.md) to understand what the DAO governs (protocol software, schemas, evidence standards) and what it explicitly does not (land ownership, disputes, legal outcomes). Follow the Founding Stewards and consider how you might participate as the protocol transitions to LGT-based Aragon DAO governance.

---

Previous: [Key Terms Glossary](08-key-terms-glossary.md)

Next: [Learn Index](README.md)
