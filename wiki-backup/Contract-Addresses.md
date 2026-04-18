# Contract Addresses

This page lists the deployed Landblock smart contract addresses across networks. All contracts are verified on Polygonscan and follow the LADM data model.

## Testnet (Polygon Amoy)

Deployed April 8, 2026, as part of Phase 2.

| Contract | Address | Purpose |
|----------|---------|---------|
| LandblockGovernance | 0x65FBa64d0E9a443fA4165D7d77252eFDdD637dEb | Protocol governance, proposals, Aragon integration |
| DummyAdminSurface | 0x15561ca6726c2DBe3631Ef4Fb4ff9730bC80C257 | Test admin interface (to be replaced post-audit) |

*Note: These are testnet deployments. Mainnet addresses will be published after Phase 7 security audit.*

## Mainnet (Polygon PoS) - Coming Soon

TBD after Phase 7 audit and mainnet launch.

| Contract | Address | Purpose |
|----------|---------|---------|
| LandblockGovernance | TBD | Protocol governance |
| LDBK Token | TBD | Utility token (21M supply, 8 decimals) |
| LGT Token | TBD | Governance token (100M supply, 18 decimals) |
| SpatialUnitRegistry | TBD | Boundary hashes and Coords URIs |
| BAUnitRegistry | TBD | Legal groupings of spatial units |
| RRRRegistry | TBD | Rights, restrictions, responsibilities |
| IdentityRegistry | TBD | SpruceID DID management |
| EvidenceStore | TBD | IPFS/Filecoin CID storage |
| RegistryDirectory | TBD | Global federation directory |
| Federation | TBD | Cross-registry verification |
| CoordsValidator | TBD | Spatial URI validation |
| PropertyToken | TBD | ERC-721/1155 fractional ownership |
| DisputeRecord | TBD | Overlapping claim management |
| LandblockPaymaster | TBD | ERC-4337 fee sponsorship |
| PrivacyVerifier | TBD | ZKP selective disclosure |

## Verification

- All contracts are built with **Foundry** and tested with invariant checks.
- Source code available in private repo (brockhager/landblock-core).
- Audits: Independent security audit scheduled for Phase 7.

## Integration

To interact with contracts:
- Use Web3 libraries (ethers.js, web3.js) or Foundry scripts.
- Polygon RPC: https://polygon-rpc.com/ (mainnet) or https://rpc-amoy.polygon.technology/ (testnet).
- Gas fees sponsored via Paymaster for registered users.

→ Next: [API Reference](API-Reference.md) | Back to [Developer Docs](Developer-Docs.md)