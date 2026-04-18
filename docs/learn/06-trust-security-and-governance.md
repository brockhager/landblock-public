# Trust, Security, and Governance

Landblock is built on a "Trust but Verify" model. The protocol uses the **Polygon PoS** blockchain and **Solidity** smart contracts verified with industry-standard security tooling.

## 1. Technical Trust (L1 Blockchain)
Unlike traditional databases, Landblock's records cannot be secretly edited by an administrator. Every update is **immutable** and **append-only** — errors are corrected via superseding events, never by modifying history.

Smart contract security is enforced through:
- **Foundry invariant tests**: Automated property-based testing that proves contracts maintain their invariants under all input combinations.
- **Slither static analysis**: Detects common vulnerability patterns before deployment.
- **ReentrancyGuard**: Applied on all state-mutating functions to prevent reentrancy attacks.
- **OpenZeppelin libraries**: Battle-tested contract primitives for access control, token standards, and upgradeability.

The LADM data model enforces structural correctness: shares on a BAUnit can never exceed 100% + 1bps, you can never assign rights directly to a SpatialUnit (must go through BAUnit), and no party can be linked to land without the proper `SpatialUnit → BAUnit → RRR → Party` traversal.

## 2. Institutional Trust (L4 Governance)
While the protocol is neutral, governance manages its development through a three-phase succession:

- **Proto-DAO** (current): The Founding Steward Multi-Sig (Gnosis Safe on Polygon PoS) authorizes protocol updates, high-level identity attestations, and emergency actions.
- **Aragon Transition**: The LGT governance token enables weighted voting. The Safe becomes an emergency veto only. This transition must complete before mainnet launch.
- **Full On-Chain Governance**: Complete LGT distribution and decentralized DAO control.

**Authority Verifiers** — government or local NGO partners — sign off on Tier 3 identity and legal recordings. They are the bridge between institutional trust and protocol trust.

## 3. Data Integrity (Commitment-Only Storage)
By storing only **cryptographic commitments** (CIDs/hashes) on the public ledger, Landblock ensures:
- **Sovereignty**: Governments keep their own private databases. On-chain data is derivative and non-authoritative.
- **Privacy**: No one can scrape the blockchain to find personal land value or coordinates. ZKP-based selective disclosure (`PrivacyVerifier.sol`) enables verification without revealing underlying data.
- **Auditability**: Every hash on-chain points to a verifiable document off-chain. Three time dimensions (valid time, system time, block timestamp) provide full temporal traceability.

## 4. Federation Security
Each registry in the federation retains **full sovereignty**. No registry can override another's records. Cross-registry verification uses cryptographic proofs (content hash, metadata hash, timestamp, ECDSA signature) without requiring trust between registries. Contested territories across jurisdictions are marked as disputed — the protocol never politically adjudicates them.

## 5. Continuity and Succession
The **Landblock Constitution** (ratified, binding) ensures that if the founding team disappears, the protocol can be managed by successors or a fully decentralized community. Trust is in the code, the LADM-compliant data model, and the governance process — not just a single company.

---

Previous: [Common Questions](05-common-questions.md)

Next: [Example Land Transfer Walkthrough](07-example-land-transfer-walkthrough.md)
