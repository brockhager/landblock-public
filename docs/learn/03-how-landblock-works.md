# How Landblock Works

This is a simplified end-to-end view.

## 1. A user or authority signs in

A participant enters through a front-end application with an authenticated identity.

## 2. A parcel workflow is started

A registration, update, transfer, or review action is initiated.

## 3. Evidence is attached and validated

Relevant documentation and verification artifacts are linked to the case.

## 4. Core modules process state changes

The protocol modules coordinate record updates, ownership state, dispute status, and related transaction handling.

## 5. The resulting state is viewable

Authorized users can inspect status and history through the appropriate application interfaces.

## Conceptual architecture view

- Front-end apps: role-specific user experiences
- Services and APIs: orchestration and policy enforcement
- Protocol modules: canonical domain behavior and records
- Data and storage layers: persistence, retrieval, and auditability

## Why this model is useful

- Clear separation of responsibilities
- Better traceability of who changed what and why
- Easier integration of policy, governance, and technical controls

---

Previous: [Core Concepts](02-core-concepts.md)

Next: [Modules and Apps](04-modules-and-apps.md)
