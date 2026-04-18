# Token Economics

Landblock uses a dual-token model to separate governance from utility, ensuring economic participation doesn't automatically confer decision-making power.

## LGT (Landblock Governance Token)

### Tokenomics
- **Symbol**: LGT
- **Standard**: ERC-20
- **Decimals**: 18
- **Total Supply**: 100,000,000 (100M)
- **Initial Distribution**: Allocated to founding stewards, contributors, and partners
- **Inflation**: None (fixed supply)

### Purpose
- **Governance**: Weighted voting in Aragon DAO
- **Treasury**: Protocol funds and grants
- **Staking**: Future incentives for active participants

### Utility
- 1 LGT = 1 vote (linear; quadratic voting TBD)
- Required for proposal submission (minimum stake)
- Can be delegated to representatives

### Distribution Plan
- **Founding Stewards**: 40% (40M LGT)
- **Contributors**: 30% (30M LGT)
- **Partners/Registries**: 20% (20M LGT)
- **Public Sale/Community**: 10% (10M LGT)
- **Vesting**: 4-year schedule with 1-year cliff

## LDBK (Landblock Utility Token)

### Tokenomics
- **Symbol**: LDBK
- **Standard**: ERC-20
- **Decimals**: 8
- **Total Supply**: 21,000,000 (21M)
- **Inflation**: None (fixed supply)
- **Burn Mechanism**: Transaction fees burned

### Purpose
- **Fees**: Platform transaction fees
- **Staking**: Liquidity provision incentives
- **Rewards**: Node operators, auditors

### Utility
- Pays for evidence anchoring, identity verification, dispute resolution
- ERC-4337 Paymaster sponsorship for users without crypto
- Deflationary: Burns reduce circulating supply

### Distribution Plan
- **Liquidity Mining**: 50% (10.5M LDBK)
- **Team/Advisors**: 20% (4.2M LDBK) - 4-year vest
- **Treasury**: 20% (4.2M LDBK)
- **Community**: 10% (2.1M LDBK)

## Economic Model

### Fee Structure
- **Base Fee**: 0.01 LDBK per transaction (Pyth oracle pricing)
- **Evidence Upload**: 0.05 LDBK per CID
- **Cross-Registry Query**: 0.02 LDBK (Federation Liaison Service)
- **Dispute Filing**: 0.1 LDBK

### Incentives
- **Liquidity Providers**: 5% APY on LDBK pools
- **Node Operators**: 10% of fees
- **Auditors**: Bounty payments in LDBK

### Treasury Management
- **Sources**: 20% of all fees
- **Uses**: Development grants, audits, marketing
- **Governance**: LGT holders vote on treasury proposals

## Market Considerations

### LGT
- **Value Driver**: Governance power in growing protocol
- **Risk**: Dilution if supply increases (currently fixed)
- **Liquidity**: DEX pools on Uniswap/Polygon

### LDBK
- **Value Driver**: Utility demand from adoption
- **Deflation**: Burns increase scarcity
- **Peg**: No peg; market-driven

## Current Status

- **Phase 2**: Tokens designed; contracts deployed on Amoy
- **Live Addresses**: LGT and LDBK contracts at TBD (post-audit)
- **Next**: Mainnet deployment and distribution

## Risks and Mitigations

- **Volatility**: Stable fee pricing via Pyth oracle
- **Adoption Lag**: Gradual rollout with Mirror Mode
- **Regulatory**: Utility token classification; no securities

→ Next: [Back to Home](../Home.md) | Back to [Governance Docs](Governance-Docs.md)