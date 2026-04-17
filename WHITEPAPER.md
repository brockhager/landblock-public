# The Landblock Whitepaper

**Version 0.4.5 — April 2026**

---

## Abstract

Land is the world's largest asset class. Yet the systems that record who owns it — land registries — remain among the least interoperable, most corruption-prone, and least trusted institutions in many countries. A family in Lima cannot easily prove to a bank in Madrid that they own their home. A government in sub-Saharan Africa cannot verify whether a foreign investor's claimed parcel overlaps with a protected indigenous territory. A court in Southeast Asia cannot access twenty-year-old records that were altered by a corrupt registrar.

Landblock is a federation protocol for land registries. It does not replace governments, courts, or land offices. It gives them a cryptographic layer so that land records — who registered what, when, with what evidence — can be verified by anyone, anywhere, without trusting any single institution.

The core insight: **blockchain verifies records; governments decide ownership.**

---

## The Problem

### Fragmentation

There is no global land registry. Every country, and often every municipality, maintains its own records in its own format. Cross-border transactions require expensive manual reconciliation. International lenders cannot efficiently verify collateral. Diaspora communities cannot easily prove inherited land rights. Development agencies cannot assess land tenure security at scale.

### Corruption and Tampering

In many jurisdictions, land records are held in paper ledgers or poorly secured databases. A corrupt official can alter, destroy, or fabricate entries. Victims often have no way to prove the original record existed. When the record-keeping institution itself is the source of fraud, there is no external check.

### Inaccessibility

Even in countries with electronic registries, records are rarely public, rarely machine-readable, and rarely accessible to the people whose lives depend on them. A smallholder farmer in a rural area has no practical way to verify that their land has not been registered under someone else's name.

### The Cost of Uncertainty

These failures are not abstract. Insecure land tenure suppresses agricultural investment, prevents access to credit, drives displacement, and fuels conflict. The World Bank estimates that insecure land tenure affects over 70% of the world's land. The economic cost is measured in trillions of dollars of locked value and foregone development.

---

## The Landblock Approach

Landblock is built on three convictions:

**1. Legal authority must stay with governments.**
Blockchain cannot and should not decide who owns land. Courts decide ownership. Governments decide law. Landblock's role is to make the record of what was claimed, registered, and evidenced tamper-resistant and publicly verifiable — not to adjudicate disputes.

**2. Adoption must be incremental.**
No government will replace its land registry overnight. Landblock is designed to be adopted in layers, starting with read-only cryptographic mirroring of existing records, and expanding to full federation as trust is established.

**3. Interoperability must be built in from the start.**
A land registry that only talks to itself has limited value. Landblock's federation protocol allows registries in different countries to verify each other's records and exchange proofs — without requiring a central authority or surrendering sovereignty.

---

## Core Principles

### Append-Only Records

Once a land record is published to Landblock, it cannot be deleted or altered. Corrections are recorded as new entries that supersede prior ones, with the full history preserved. This creates an auditable chain: every version of a record, every correction, every dispute is permanently visible.

### Cryptographic Evidence Binding

Physical evidence — survey documents, community letters, photos, court orders — is stored off-chain (on IPFS) but cryptographically bound to on-chain records. The content cannot be altered without invalidating the binding. If someone claims a parcel has evidence attached, that evidence can be independently verified.

### Bitemporal Versioning

Landblock distinguishes between three time dimensions for every record:
- **Valid time**: when the fact was true in the real world
- **System time**: when Landblock recorded it
- **Block time**: when the Polygon blockchain confirmed it

This matters when records are corrected retroactively, when evidence is submitted late, or when disputes arise about what was known when. Bitemporal records make these distinctions precise and auditable.

### Government Sovereignty

Landblock is not a jurisdiction. It does not impose legal interpretations on the records it stores. A registry that publishes records to Landblock retains full authority over what those records mean legally. Landblock proves what was published — not what it means.

### Privacy by Design

Not all land information should be public. Landblock implements a three-tier disclosure framework: records can be marked public (fully visible), restricted (metadata visible, content gated), or sealed (existence only). Cross-registry evidence exchange respects these tiers. Zero-knowledge proofs allow verification without revelation — a lender can verify land ownership without the registry revealing the underlying record data.

---

## How Landblock Works

### Registries and Parties

In Landblock's model, a **registry** is any institution authorized to publish land records — a national land authority, a municipal cadastre, a customary land office, or a development agency. Each registry maintains its own records and publishes cryptographic proofs to the Landblock network.

A **party** is a person or organization with a land-related role: owner, trustee, mortgagee. Parties are identified using decentralized identifiers (DIDs), which allow identity to be verified across registries without a central identity provider.

### Spatial Units and Basic Administrative Units

A **spatial unit** is a physical area of land, defined by coordinates and validated against the CoordsApp coordinate specification. A **Basic Administrative Unit (BAUnit)** is the legal entity that holds rights — it may encompass one or more spatial units. This separation follows the ISO 19152 Land Administration Domain Model (LADM), an international standard for land administration systems.

### Rights, Restrictions, and Responsibilities

Every legal relationship between a party and a BAUnit — ownership, lease, mortgage, easement, restriction — is recorded as an RRR (Right, Restriction, or Responsibility). RRRs have a full lifecycle: granted, transferred, suspended, reactivated, terminated. Share accounting tracks fractional ownership. Temporal validity tracks when rights are active.

### Evidence

Evidence — the documents, photos, surveys, and community attestations that support a land claim — is recorded in the EvidenceStore. Each evidence record includes a full temporal envelope and can supersede prior records. Evidence is stored on IPFS; only the cryptographic commitment is on-chain.

---

## The Federation Protocol

The federation protocol is what makes Landblock more than a single registry. It allows multiple registries to interoperate while maintaining sovereignty.

### Registry Accreditation

Registries join the Landblock network by being accredited to a conformance tier:
- **Mirror**: read-only; publishes proofs of its records
- **Verified**: full participation; records can be cross-referenced
- **Full Federation**: bidirectional; registries can establish direct federation links and exchange proofs

Accreditation is governed by the Landblock DAO. It can be suspended or revoked if a registry fails to maintain standards.

### Federation Functions

Landblock defines five federation functions:

**Function 1 — Proof Publication**: A registry publishes a cryptographic proof that a record exists, linking it to evidence and a trust context.

**Function 2 — Cross-Registry Verification**: A registry requests verification of a proof from another registry, establishing a trust context (direct federation, shared accreditor, or third-party attestation).

**Function 3 — DID Identity Resolution**: A registry resolves a decentralized identity across registries, with full provenance — who issued it, when, through what chain of authority.

**Function 4 — Evidence Exchange**: Registries exchange evidence with disclosure tier controls. A restricted record shares metadata but not content. A sealed record confirms existence only.

**Function 5 — Lending Verification**: A lending institution requests proof of land ownership without the registry revealing the underlying record. The result is a cryptographic verification — owns, does not own, boundary dispute present — without exposing sensitive data.

### The Federation Liaison Service

Cross-registry queries do not always resolve automatically. The Federation Liaison Service routes queries through three tiers:
- **Tier 1**: AI-automated routing for standard, unambiguous queries
- **Tier 2**: A facilitated channel for queries requiring human review, with DID-authenticated messaging and on-chain outcome recording
- **Tier 3**: Escalation to human operators for complex disputes

---

## Mirror Mode: Incremental Adoption

The most common objection to blockchain-based land systems is that they require wholesale replacement of existing institutions. Landblock rejects this model.

**Mirror Mode** allows a registry to participate in Landblock without changing any internal workflow. The registry continues operating exactly as it does today. At regular intervals — daily, weekly — it publishes a cryptographic proof of its current record state to Landblock. No data moves. No process changes. No sovereignty is transferred.

The value is immediate: anyone can verify that the registry's records have not been altered since the last proof. Foreign lenders, development agencies, and courts gain a tamper-evident audit trail without the registry giving up control.

Over time, a registry can progress from Mirror Mode to Verified participation to Full Federation — at its own pace, driven by its own assessment of the benefits.

---

## Governance

### The Constitution

Landblock is governed by a ratified Constitution, currently at version 0.4.5. The Constitution establishes the principles that cannot be changed by ordinary governance — including that Landblock will never make decisions about land outcomes, that protocol changes require supermajority approval, and that founding stewards retain emergency veto power during the early phase of the project.

### The DAO

Ongoing governance is handled by the Landblock DAO, implemented on Aragon on Polygon. Governance token holders (LGT) vote on protocol changes, registry accreditation decisions, and other matters within the DAO's scope. The DAO's scope is explicitly limited to the protocol — it never makes decisions about specific land parcels or ownership outcomes.

### The Two-Token Model

**LGT (Landblock Governance Token)** is the voting token. It is distributed to founding stewards, contributors, and registered partners.

**LDBK (Landblock Utility Token)** is the economic token, used for protocol fees and incentives. It has no governance rights.

This separation ensures that economic participation does not automatically confer governance power.

### The Neutrality Lock

A registry that joins Landblock cannot be discriminated against based on the country it operates in, the legal system it uses, or the political context it exists within — provided it meets the technical conformance standards. This neutrality is protected by a constitutional provision requiring 85% supermajority approval and a 90-day review window to modify.

---

## The Peru Pilot

The reference implementation for Landblock's first government pilot is Peru's land administration system.

**SUNARP** (Superintendencia Nacional de los Registros Publicos) is the national property registry. It holds formal title records for urban and peri-urban properties and is the legally authoritative source of ownership in Peru.

**COFOPRI** (Organismo de Formalizacion de la Propiedad Informal) manages the formalization of informal settlements — the process by which families occupying land without formal title obtain legal recognition.

The Peru pilot targets two integration paths:

**Path A — SUNARP Mirror Mode**: SUNARP publishes cryptographic proofs of its title records to Landblock. No workflow change. Immediate verifiability for foreign lenders and international transactions.

**Path B — COFOPRI Tenure Conversion Workflow**: The seven-stage tenure conversion process is instrumented at each stage. Evidence is cryptographically bound at each transition. The result is an auditable, verifiable record of the full formalization process.

---

## Technical Foundation

Landblock is built on:

- **Polygon PoS**: A production-grade EVM-compatible blockchain with low transaction costs and established institutional adoption
- **Solidity / OpenZeppelin**: Industry-standard smart contract tooling
- **IPFS**: Decentralized content-addressed storage for evidence files
- **The Graph**: Indexed query layer for efficient data access
- **ISO 19152 LADM**: International Land Administration Domain Model, ensuring compatibility with global GIS and cadastral standards
- **SpruceID / W3C DIDs**: Decentralized identity standards for cross-registry party identification

---

## Roadmap

| Phase | Description | Status |
|-------|-------------|--------|
| 1 | Constitution ratified | Complete |
| 2 | Governance contracts and DAO setup | In Progress |
| 3 | Core federation contracts on testnet | Complete |
| 4 | Full federation functions + subgraph + lending API | Complete |
| 5 | Federation Liaison Service | Next |
| 6 | Registry template for government deployment | Next |
| 7 | Peru pilot + production hardening + security audit | Next |
| 8 | Full DAO activation + CoordsApp integration | Next |

---

## What This Is Not

Landblock is not:
- A cryptocurrency or financial product
- A replacement for legal land title
- A system that decides ownership disputes
- A surveillance tool for tracking individuals
- A way for any single entity to control land records globally

---

## Conclusion

The world's land record systems are broken in ways that cost billions of people security, access to credit, and protection from displacement. The solution is not to replace those systems — it is to give them a trustworthy mirror, a way to prove what they recorded and when, and a protocol for speaking to each other.

Landblock is that protocol. It is neutral by design, incremental by necessity, and governed by the people building it — not by any government, corporation, or blockchain investor.

The goal is simple: a world where anyone, anywhere, can verify a land record — and where no one can quietly make one disappear.

---

*This whitepaper reflects the current state of the Landblock project as of April 2026. It is not a specification, a legal document, or an investment prospectus.*
