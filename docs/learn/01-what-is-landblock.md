# What Is Landblock?

Landblock is a blockchain-based **federation protocol for land registries** — a shared trust layer that allows registries worldwide to publish cryptographic proofs, verify each other's records, and cooperate across jurisdictions without surrendering sovereignty.

In simple terms, it helps record who owns what land and what evidence supports that ownership — without ever replacing the legal authority of governments or courts. Registries keep their authority; Landblock provides the interoperability infrastructure.

## The Problem

Traditional land systems often struggle with:
- **Tamper Risk**: Paper records can be altered, lost, or forged.
- **Fragmented Data**: Information is stuck in silos and hard to verify across borders. 70%+ of Africa's land is informally held; fraud occurs in 30% of transactions in emerging markets.
- **Low Trust**: High friction and fraud risk when records aren't transparently verifiable. 60% of Indian court cases involve land disputes; $6T+ in dead capital exists in Latin America alone.

## The Landblock Approach

Landblock provides a three-layer federation architecture:

1. **Global Directory** — A shared on-chain registry of registries, so any participant can discover and verify any other.
2. **Federation Protocol** — Cross-registry verification and proof exchange without semantic harmonization.
3. **Registry Layer** — Each existing registry (or a new one using the Landblock Registry Template) publishes cryptographic proofs of its records.

All of this runs on **Polygon PoS** with ~2-second finality and near-zero fees, using **Solidity** smart contracts that comply with the **ISO 19152 LADM** international land administration standard.

Records on Landblock are:
- **Immutable**: Once a record is "anchored" to the blockchain, it cannot be secretly altered.
- **Verifiable**: Anyone with permission can check the cryptographic proof of a claim.
- **Private**: Only cryptographic commitments (hashes) are stored on-chain. Sensitive PII and land geometry stay off-chain under sovereign control.

## What Landblock Is NOT

- **Not a replacement for courts**: Courts still decide who "owns" land.
- **Not a sovereign database**: Governments still maintain their own private records.
- **Not a legal authority**: The protocol never assumes governance, adjudication, or enforcement authority.
- **Not a title issuance system**: Landblock records attestations, not legal title.

Landblock provides **technical trust** so that institutions can focus on **legal truth**.

> "Adopting Landblock does not require you to trust the blockchain; it only requires you to publish your attestations to it."

---

Next: [Core Concepts](02-core-concepts.md)
