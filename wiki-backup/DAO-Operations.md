# DAO Operations

This page details how the Landblock DAO operates, from proposal submission to execution. The DAO uses Aragon for governance, with LGT tokens for voting.

## Current Phase: Proto-DAO

- **Controller**: Founding Steward Multi-Sig (Gnosis Safe on Polygon PoS).
- **Authority**: Approves protocol updates, identity attestations, emergency actions.
- **Transition**: Moves to LGT voting after Phase 7 audit.

## Proposal Lifecycle

### 1. Draft Phase
- **Who**: Any LGT holder or registered participant.
- **How**: Submit via Aragon interface or GitHub discussion.
- **Requirements**: Clear description, impact assessment, implementation plan.
- **Duration**: Open for community feedback (7-14 days).

### 2. Discussion Phase
- **Forum**: GitHub Discussions or Aragon forum.
- **Review**: Technical review by core team; legal review if needed.
- **Amendments**: Proposer can revise based on feedback.
- **Duration**: 7 days minimum.

### 3. Voting Phase
- **Eligibility**: LGT holders (1 LGT = 1 vote; no quadratic yet).
- **Options**: For/Against/Abstain.
- **Quorum**: 10% of circulating LGT.
- **Threshold**: Simple majority (50% +1) for routine; 85% for constitutional changes.
- **Duration**: 7 days.

### 4. Execution Phase
- **If Passed**: Core team implements within 30 days.
- **If Failed**: Can resubmit after 30 days with revisions.
- **Transparency**: All votes and outcomes recorded on-chain.

## Emergency Procedures

- **Trigger**: Critical security issue or protocol halt.
- **Authority**: Founding Multi-Sig can execute emergency actions.
- **Review**: Post-action audit and community vote to ratify.
- **Sunset**: Emergency powers expire at full DAO activation.

## Aragon Integration

- **Platform**: Aragon Client on Polygon PoS.
- **Voting**: LGT-weighted; future quadratic voting possible.
- **Treasury**: Managed via Aragon Finance app.
- **Plugins**: Custom plugins for land-specific governance (TBD).

## Participation

### Becoming a Voter
1. Acquire LGT tokens (from founding distribution or market).
2. Connect wallet to Aragon.
3. Delegate voting power if desired.

### Roles
- **Token Holders**: Vote on proposals.
- **Delegates**: Represent community interests.
- **Core Team**: Execute approved proposals.
- **Auditors**: Independent security reviews.

## Metrics and Reporting

- **Active Proposals**: Tracked in Aragon dashboard.
- **Voting Participation**: Public on-chain.
- **Treasury Balance**: Transparent via Polygon explorer.
- **Quarterly Reports**: Governance activity summaries.

## Best Practices

- **Inclusive**: Encourage diverse participation.
- **Transparent**: All discussions public.
- **Efficient**: Use off-chain discussions to refine proposals.
- **Secure**: Multi-sig execution for high-value actions.

## Current Status

- **Phase 2**: Governance contracts deployed on Amoy.
- **Live**: LandblockGovernance at 0x65FB..., DummyAdminSurface at 0x1556...
- **Next**: Aragon activation and LGT distribution.

→ Next: [Token Economics](Token-Economics.md) | Back to [Governance Docs](Governance-Docs.md)