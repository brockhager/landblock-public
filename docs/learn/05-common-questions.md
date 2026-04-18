# Common Questions (FAQ)

## Is my land data public on the blockchain?
No. Landblock follows a binding **"Commitment-Only Storage"** design invariant. We only store cryptographic hashes (CIDs) of your documents and geometry. The chain never holds full record content. To see the actual data, someone needs the original file and permission to view it. Hashes are treated as opaque — you can't reverse-engineer coordinates or personal details from them.

## Do I have to pay for every transaction (Gas)?
No. Landblock includes a **Paymaster** (`LandblockPaymaster.sol`) that uses **ERC-4337 Account Abstraction** to sponsor gas fees for registered users. This means the experience feels like a traditional app — you don't need to buy cryptocurrency to use the system.

## What are the LDBK and LGT tokens?
Landblock uses a **dual-token model**:
- **LDBK** (21M fixed supply): A utility token used for platform fees, staking, and liquidity mining. It has no governance voting power and is deflationary via burns.
- **LGT** (100M initial supply): A governance token used for DAO proposals, voting, and treasury management. LGT holders govern how the protocol operates (but never the land records themselves).

## What if the government doesn't recognize Landblock?
Landblock operates across three **Conformance Tiers**. At Tier 1 (Mirror Mode), Landblock acts as an independent cryptographic backup and audit trail — the registry publishes proofs without needing to change any of its existing processes. This provides tamper-evidence for citizens even before the protocol is officially adopted. As trust grows, registries can progress to Tier 2 (Verified) and Tier 3 (Full) for cross-registry interoperability.

## How do you prevent someone from recording a fake parcel?
We use a **Tier 1–3 Identity** system:
- **Tier 1**: Self-asserted (lowest weight).
- **Tier 2**: Verified by 3 community witnesses.
- **Tier 3**: Verified by a legal authority — government or court (highest legal weight).

A record's credibility is directly tied to its attestation tier. Additionally, the `DisputeRecord.sol` contract automatically flags overlapping claims, and cross-registry federation verification can catch inconsistencies across jurisdictions.

## What happens if I lose my private key?
Because Landblock uses **SpruceID DIDs** for identity, we support **Identity Recovery** through the Founding Steward Multi-Sig or authorized recovery partners. Your DID and its associated records are not lost just because a single key is compromised.

## What standards does Landblock follow?
Landblock is designed to comply with:
- **ISO 19152 LADM** — The international land administration domain model
- **OGC** — Open Geospatial Consortium standards for spatial data
- **UN-GGIM FELA** — Framework for Effective Land Administration
- **FAO VGGT** — Voluntary Guidelines on Governance of Tenure
- **World Bank LGAF** — Land Governance Assessment Framework

## How does the DAO work?
Governance follows a three-phase succession:
1. **Proto-DAO** (current): Founding Steward Multi-Sig (Gnosis Safe on Polygon PoS) authorizes protocol changes.
2. **Aragon Transition**: LGT token deployed, LGT-weighted voting activated, Safe becomes emergency veto only. Must complete before mainnet.
3. **Full On-Chain Governance**: Complete LGT distribution and full Aragon DAO control.

The DAO governs protocol software, data schemas, and evidence standards. It **never** governs parcel ownership, competing claims, or specific land outcomes.

---

Previous: [Modules and Apps](04-modules-and-apps.md)

Next: [Trust, Security, and Governance](06-trust-security-and-governance.md)
