# The Landblock Protocol Governance Constitution
**Phase 1: Proto-DAO Foundation**
**Version: v0.4.5**

---

## Version History

| Version | Date | Summary |
|---------|------|---------|
| v0.1 | 04-03-2026 | Initial ratification — founding steward |
| v0.3 | 04-05-2026 | Re-ratified — Polygon PoS migration |
| v0.4.5 | Apr 2026 | Amended — two-token model (LGT/LDBK); updated succession plan; neutrality lock threshold specified; ADR governance principle added |

---

## Article 0: Foundational Purpose (Immutable)

### Landblock Foundational Purpose
Landblock provides an immutable, auditable **cryptographic verification layer** for land records, enabling governments to mirror, verify, and selectively adopt blockchain-based integrity guarantees without disrupting existing legal authority or administrative workflows.

### Governing Principle (Non-Negotiable)
1. **Sovereignty**: The authoritative land registry remains unchanged and sovereign.
2. **Role**: Blockchain provides verification, resilience, and transparency — not governance of the land itself.
3. **Immutability**: This Article is non-revisable and serves as the highest-level constraint for all protocol development.

---

## Preamble: The Governing Principle
Courts and governments decide what is true about land. The Landblock Protocol DAO decides only how truth can be recorded. These domains must never overlap.

---

## 1. Scope Boundaries: What the DAO Governs vs. Does Not Govern

The DAO retains strict legislative authority over the software and standards of the protocol. It permanently relinquishes any authority over real-world land outcomes.

| Category | The DAO **Governs** (In Scope) | The DAO **Does NOT Govern** (Out of Scope) |
| :--- | :--- | :--- |
| **Decisions** | Protocol software versions and upgrade processes | Who owns any specific parcel |
| **Standards** | Data schema evolution and compatibility rules | Which competing claim is legally correct |
| **Evidence** | Evidence type standards and boundary format specs | The legal validity of any recorded evidence |
| **Identity** | Identity tier definitions and attestation standards | Whether a specific person owns specific land |
| **Operations** | Node operator requirements and replacement | How any government uses Landblock data internally |
| **Security** | Cryptographic assumptions and audit requirements | The internal policies of any adopting jurisdiction |
| **Neutrality** | Neutrality constraints binding all participants | Any land outcome in any jurisdiction |
| **Routing** | Federation Liaison Service routing model and facilitated channel design | What evidence a registry chooses to share through the facilitated channel |

---

## 2. Three-Layer Authority Model

To ensure no single entity can corrupt the property layer, authority is bifurcated into sovereign truth and protocol operations.

1. **Layer 1: External Sovereign Authority**
   - **Scope:** Defines who owns land, the legal validity of instruments, and the outcomes of disputes.
   - **Governed By:** External Courts, Governments, and Legally Recognized Bodies.

2. **Layer 2: Protocol Rules (The DAO)**
   - **Scope:** Defines data schemas, structural upgrades, absolute neutrality constraints, and federation standards.
   - **Governed By:** The Landblock Protocol DAO (LGT token holders and Stewards).

3. **Layer 3: Operations**
   - **Scope:** Responsible for node operation, indexing the chain, providing UI wrappers, and physical maintenance.
   - **Governed By:** Operators (who are bound strictly by Layer 2 and are entirely replaceable without breaking the network).

---

## 3. Succession Plan & Path to On-Chain Governance

Landblock dictates a deliberate migration path for governance tooling. The rules of this Constitution remain constant; only the execution environment changes to increase decentralization over time.

### Step 1: Phase 1 — The Proto-DAO (Current)
- **Tooling:** This written Governance Constitution + Founding Steward Gnosis Safe on Polygon PoS.
- **Rationale:** Ensures explicit alignment and human readability before cementing power into an automated on-chain environment. Prevents early "code-is-law" governance failures (e.g., Bitland).

### Step 2: Phase 2 — Aragon Transition
- **Tooling:** Deploy `LGTToken.sol` on Polygon PoS. Configure Aragon voting plugin to reference LGT. Distribute LGT to founding stewards. Transition Gnosis Safe to emergency veto role only.
- **Rationale:** LGT (Landblock Governance Token) is the dedicated governance voting token. LDBK is utility-only. Separating governance influence from economic activity protects protocol neutrality. Aragon on Polygon PoS provides a mature, audited governance framework with token-weighted voting on the same chain as the protocol — no cross-chain complexity, no bridge risk.
- **Prerequisite:** Must be completed before mainnet launch.

### Step 3: Phase 3 — Full On-Chain Governance
- **Tooling:** Full LGT distribution across all three allocation buckets (founding stewards, active registry participants, contributors). Complete transition to Aragon. Gnosis Safe M-of-N emergency veto threshold set by DAO vote at transition.
- **Rationale:** The ultimate end-state. Governance is fully decentralized, token-weighted, and on-chain. The emergency veto multi-sig remains as a last-resort safeguard only.

---

## 4. Token Model

> **Amended in v0.4.5** — Two-token model replaces single LDBK model.

The Landblock Protocol uses two separate tokens with distinct purposes. Governance influence is not purchasable via the utility token.

### 4.1 LDBK — Landblock Token (Utility)
The **LDBK** token is the platform utility token. It confers:
1. **Fee payments:** Used to pay query fees and federation service fees.
2. **Fee discounts:** Reduced costs for transaction operations.

LDBK has **no governance voting rights.**

### 4.2 LGT — Landblock Governance Token
The **LGT** token is the DAO governance token. It confers:
1. **Governance voting:** The exclusive right to vote on Layer 2 Protocol Rules as defined in this Constitution, via Aragon on Polygon PoS.

LGT is **not transferable into governance power via LDBK.** There is no direct exchange mechanism between the two tokens at this stage.

**Distribution — three buckets:**
| Bucket | Recipients | Mechanism |
|---|---|---|
| Founding stewards | Protocol builders and launchers | Grant with vesting schedule |
| Active registry participants | Registries publishing proofs and participating in governance | Earned through participation |
| Contributors | Developers, researchers, Library curators, community | DAO working group allocation |

Specific percentages and vesting schedules are deferred to Phase 2 / Phase 3 — set when network size is known. Annual review by DAO. All changes subject to ADR and DAO vote.

---

## 5. Neutrality Lock

The neutrality clause — that the DAO governs the protocol only, never land outcomes — is the foundational constraint of this Constitution. It is protected by a constitutional supermajority:

- **Amendment threshold:** 85% of all circulating LGT (not just participating voters).
- **Deliberation window:** Minimum 90 days before a vote on any neutrality amendment can close.
- **Self-protecting:** Lowering either the 85% threshold or the 90-day window requires the same 85% + 90-day process — plus an ADR and DAO vote.

No majority, however large, can amend the neutrality clause without this full process. This is intentional and permanent.

---

## 6. Architecture Decision Record (ADR) Governance Principle

Any change to a resolved design decision requires:
1. A formal DAO vote (LGT-weighted, via Aragon on Polygon PoS once Phase 2 is complete; via founding steward multi-sig in Phase 1).
2. A corresponding Architecture Decision Record documenting the decision, rationale, alternatives considered, and vote outcome.

This applies to all design decisions resolved in v0.4 and beyond, and to any future amendments to this Constitution. Good reason is required. The ADR record is permanent and on-chain once Phase 2 is complete.

---

## Signatures (Founding Stewards)
*By signing this document, the stewards irrevocably commit the Landblock Protocol to the neutrality and boundary definitions contained herein.*

- [x] **Steward 1:** ___Brock Hager_____________  Date: _04-03-2026_  *(Original — v0.1)*
- [x] **Steward 1:** ___Brock Hager_____________  Date: _04-05-2026_  *(v0.3 — Polygon PoS migration re-ratification)*
- [ ] **Steward 1:** ___Brock Hager_____________  Date: _04-14-2026_  *(v0.4.5 — two-token model; succession plan; neutrality lock; ADR principle)*

---

*— End of Constitution v0.4.5 —*
