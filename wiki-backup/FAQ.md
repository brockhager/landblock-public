# FAQ

Frequently asked questions about Landblock. If your question isn't here, check the [Community & Participation](Community-and-Participation.md) page or open a discussion.

## General Questions

### What is Landblock?
Landblock is a blockchain-based federation protocol that connects sovereign land registries without replacing them. It provides cryptographic proofs and shared trust for cross-jurisdiction land verification.

### Why blockchain for land records?
Blockchain offers immutable audit trails and decentralized verification. Unlike traditional databases, records can't be secretly altered, and anyone can check integrity without trusting a single authority.

### How is Landblock different from other land blockchain projects?
Most projects (like Bitland) try to replace registries entirely, which governments reject due to sovereignty concerns. Landblock federates existing registries incrementally — they keep control, we add trust.

### Is Landblock a cryptocurrency?
No. It's a protocol for land records. We use tokens (LGT for governance, LDBK for fees) but the core value is in verified land data, not speculation.

## Adoption & Sovereignty

### Do governments have to change their systems?
No. Landblock's "Mirror Mode" lets registries publish proofs without altering workflows. Adoption starts with read-only verification and progresses at their pace.

### What if a government doesn't recognize blockchain?
Landblock operates in three tiers: Mirror (proofs only), Verified (bilateral checks), Full Federation. Even without recognition, it provides tamper-evident backups.

### Can Landblock be used in any country?
Yes. The protocol is neutral — no discrimination by legal system or politics. Registries adopt based on technical standards, not geopolitics.

### Who decides land ownership?
Courts and governments always decide ownership. Landblock verifies how records are stored and shared — not what they mean legally.

## Technical Questions

### What blockchain does Landblock use?
Polygon PoS — an EVM-compatible chain with ~2-second finality, low fees, and Ethereum security via checkpoints.

### Are land coordinates stored on-chain?
No. Only cryptographic hashes ("Boundary Hashes") are on-chain. Actual geometry stays off-chain under registry control.

### How do you handle privacy?
Three-tier disclosure: Public (open), Restricted (gated), Sealed (existence-only). Registries control access; ZKP enables verification without revealing data.

### What standards does Landblock follow?
ISO 19152 LADM (international land model), OGC geospatial standards, and W3C DIDs. Designed for compatibility with global cadastral systems.

### How does the Federation Liaison Service work?
A three-tier system: AI-automated routing, facilitated human review, and escalated dispute resolution. Ensures cross-registry queries are efficient and fair.

## Tokens & Economics

### What are LGT and LDBK?
- **LGT**: Governance token (100M supply). Used for DAO voting and treasury.
- **LDBK**: Utility token (21M supply). Pays fees; deflationary via burns.

### Do I need cryptocurrency to use Landblock?
No. ERC-4337 Account Abstraction sponsors gas fees for registered users.

### How are fees priced?
Via Pyth oracle for USD/MATIC/LDBK rates. Fees are burned to reduce supply.

## Governance & Participation

### How does the DAO work?
LGT holders vote on protocol changes via Aragon. The DAO governs software/schemas/standards — never land outcomes.

### What can't the DAO change?
The Constitution (v0.4.5) locks core principles: sovereignty, neutrality, and scope boundaries.

### How can I participate?
Hold LGT for voting, contribute to discussions, or join as a registry/registry operator. See [Community & Participation](Community-and-Participation.md).

## Security & Risks

### Has Landblock been audited?
Independent audit scheduled for Phase 7. Contracts use Foundry testing, Slither analysis, and OpenZeppelin libraries.

### What are the risks?
Blockchain volatility, adoption challenges, regulatory uncertainty. Mitigated by incremental rollout and neutrality design.

### What happens if there's a dispute?
Disputes are recorded on-chain but resolved off-chain by authorities. The protocol marks conflicts — it doesn't adjudicate.

## Next Steps

Still have questions? Check:
- [How It Works](How-It-Works.md) for technical overview
- [Roadmap](Roadmap.md) for project status
- [Developer Docs](Developer-Docs.md) for integration

→ Back to [Home](Home.md)