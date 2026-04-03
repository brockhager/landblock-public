# Modules and Apps

This page is the canonical beginner map of named protocol modules and front-end applications.

## Core Protocol Modules

1. landblock.parcel-registry
Purpose: Maintains parcel records and parcel lifecycle state.

2. landblock.identity
Purpose: Handles trusted identity representation and related verification hooks.

3. landblock.evidence-store
Purpose: Stores and links evidence artifacts used in claims and reviews.

4. landblock.dispute-record
Purpose: Tracks disputes, statuses, and associated records.

5. landblock.property-token
Purpose: Represents property rights/state in tokenized form within the protocol model.

6. landblock.gas-station
Purpose: Supports transaction fee handling and smoother user operations for supported flows.

## Front-End Applications

1. Landblock Register
Purpose: Main workflow interface for registration and record updates.

2. Landblock Explorer
Purpose: Discovery and inspection interface for parcel and record visibility.

3. Landblock Investor
Purpose: Investor-oriented interface for evaluating relevant land-linked opportunities and status.

## How they connect

- Apps call service and API layers.
- Service and API layers invoke module logic.
- Module outputs become the source of truth for system state and history.

---

Previous: [How Landblock Works](03-how-landblock-works.md)

Next: [Common Questions](05-common-questions.md)
