# Modules and Apps

This page is the canonical beginner map of named protocol modules and front-end applications.

## Core Protocol Modules

The protocol consists of 9 Solidity modules:

1. Registry
Purpose: Maintains parcel records and parcel lifecycle state.

2. Identity
Purpose: Handles trusted identity representation and related verification hooks. Uses SpruceID DIDs with tiered attestations.

3. Evidence
Purpose: Stores and links evidence artifacts used in claims and reviews. Evidence stored off‑chain (IPFS) but cryptographically bound on‑chain.

4. Disputes
Purpose: Tracks disputes, statuses, and associated records. Disputes recorded as lifecycle events.

5. Tokens
Purpose: Represents property rights/state in tokenized form within the protocol model.

6. Gas Station
Purpose: Supports transaction fee handling and smoother user operations for supported flows.

Additional modules handle governance, indexing, and other core functions.

## Front-End Applications

1. **Register** (React Native, offline‑first)
Purpose: Main workflow interface for registration and record updates.

2. **Explorer** (Next.js, public verification)
Purpose: Discovery and inspection interface for parcel and record visibility.

3. **Investor** (tokenized property access)
Purpose: Investor-oriented interface for evaluating relevant land-linked opportunities and status.

## How they connect

- Apps call service and API layers.
- Service and API layers invoke module logic.
- Module outputs become the source of truth for system state and history.

---

Previous: [How Landblock Works](03-how-landblock-works.md)

Next: [Common Questions](05-common-questions.md)
