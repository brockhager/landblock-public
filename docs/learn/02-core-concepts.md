# Core Concepts

This page explains the basic ideas you need before looking at architecture details.

## Parcel

A parcel is a unit of land represented in the system with identifying details and boundaries.

## Identity

An identity represents a person, organization, or authority interacting with the platform.

Landblock identity flows are designed to support trusted verification while limiting unnecessary data exposure. Uses SpruceID DIDs with tiered attestations.

## Evidence

Evidence is supporting material tied to a parcel or claim, such as documents, images, or verification artifacts.

Evidence is stored off‑chain (IPFS) but cryptographically bound on‑chain.

## Dispute

A dispute is a formal record that ownership, boundaries, or claim validity is contested.

Disputes are recorded as lifecycle events. Disputes are tracked so reviewers can see process status, evidence, and outcomes.

## Property Token

A property token is a digital representation linked to parcel state and ownership rights inside the system model.

## Gas and Transaction Fees

Operational actions in protocol systems usually require transaction fees. Landblock includes a gas station component to simplify fee handling in supported flows.

## Append-Only Records

Landblock uses immutable claims, not mutable state. All records are append-only parcel assertions.

## Mirror Mode

A mode where governments can publish cryptographic proofs of their land registries daily, allowing incremental adoption without disrupting workflows.

## Applications vs Protocol Modules

- Protocol modules define core system behavior and records (9 Solidity modules: registry, identity, evidence, disputes, tokens, gas station).
- Front-end applications provide user interfaces for specific workflows (Register app, Explorer app, Investor app).

Think of modules as the engine, and apps as dashboards and controls.

---

Previous: [What Is Landblock?](01-what-is-landblock.md)

Next: [How Landblock Works](03-how-landblock-works.md)
