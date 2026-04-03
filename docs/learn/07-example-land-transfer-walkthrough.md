# Example Land Transfer Walkthrough

This page gives a beginner-friendly scenario showing how Landblock components work together.

## Scenario

A seller wants to transfer ownership of a parcel to a buyer.

## Step 1: Identities are verified

Both parties use trusted identities so the system can verify who is submitting and approving actions.

Related module: `landblock.identity`

## Step 2: Parcel record is retrieved

The current parcel state is loaded, including ownership status and linked records.

Related module: `landblock.parcel-registry`

## Step 3: Evidence is attached

Required documents for the transfer are uploaded and linked to the process.

Related module: `landblock.evidence-store`

## Step 4: Transfer action is submitted

A state transition is requested to reflect ownership change according to policy rules.

Related module: `landblock.property-token`

## Step 5: Fees are handled

Transaction fees are processed through supported fee workflows.

Related module: `landblock.gas-station`

## Step 6: Dispute path remains available

If any party contests details, the case can move into a formal dispute process.

Related module: `landblock.dispute-record`

## Step 7: Result is visible in apps

Authorized users can view updated state and history through front-end applications.

- Landblock Register for workflow operations
- Landblock Explorer for record visibility
- Landblock Investor for investor-oriented views

## Why this matters

This flow shows how identity, parcel state, evidence, governance, and transaction handling connect to create traceable ownership updates.

---

Previous: [Trust, Security, and Governance Basics](06-trust-security-and-governance.md)

Next: [Key Terms Glossary](08-key-terms-glossary.md)

Start over: [Landblock Learning Path](README.md)
