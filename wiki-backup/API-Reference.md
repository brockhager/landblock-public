# API Reference

This page documents the Landblock API endpoints for querying indexed data. Landblock uses **The Graph** for subgraph indexing on Polygon, providing efficient read access to on-chain data without direct blockchain queries.

## Base URLs

- **Testnet (Amoy)**: https://api.thegraph.com/subgraphs/name/brockhager/landblock-amoy
- **Mainnet (PoS)**: TBD (after Phase 8 mainnet launch)
- **Explorer UI**: https://thegraph.com/explorer/subgraph/brockhager/landblock-amoy

## Core Entities

Landblock's API follows the ISO 19152 LADM data model. All queries return data in LADM-compliant JSON format.

### SpatialUnit
Represents a physical land parcel.

**Fields:**
- `id`: Unique identifier (Coords L1 URI)
- `boundaryHash`: Cryptographic fingerprint of geometry
- `createdAt`: System timestamp
- `updatedAt`: Last modification timestamp

**Example Query:**
```graphql
{
  spatialUnits(first: 10) {
    id
    boundaryHash
    createdAt
  }
}
```

### BAUnit
Legal grouping of SpatialUnits.

**Fields:**
- `id`: Unique BAUnit ID
- `spatialUnits`: Array of associated SpatialUnit IDs
- `createdAt`: System timestamp

**Example Query:**
```graphql
{
  baUnits(where: { id: "0x123..." }) {
    id
    spatialUnits {
      id
      boundaryHash
    }
  }
}
```

### RRR (Rights, Restrictions, Responsibilities)
Rights attached to BAUnits.

**Fields:**
- `id`: Unique RRR ID
- `baUnit`: Associated BAUnit ID
- `party`: Owner DID
- `rightType`: Ownership, lease, etc.
- `share`: Fractional share (0-10000 basis points)
- `validFrom`: Valid time start
- `validTo`: Valid time end

**Example Query:**
```graphql
{
  rrrs(where: { baUnit: "0x123..." }) {
    id
    party
    rightType
    share
  }
}
```

### Party
Identities (people/organizations).

**Fields:**
- `id`: DID identifier
- `tier`: Identity verification level (1-3)
- `createdAt`: Registration timestamp

### Evidence
Supporting documents.

**Fields:**
- `id`: Unique evidence ID
- `cid`: IPFS/Filecoin content identifier
- `recordId`: Associated record ID
- `createdAt`: Upload timestamp

### Dispute
Overlapping claims.

**Fields:**
- `id`: Dispute ID
- `spatialUnit`: Affected SpatialUnit
- `parties`: Involved DIDs
- `status`: Open/Resolved
- `createdAt`: Dispute timestamp

## Federation Queries

### RegistryDirectory
List of participating registries.

**Fields:**
- `id`: Registry ID
- `name`: Registry name
- `tier`: Conformance tier
- `endpoint`: Federation API endpoint

**Example Query:**
```graphql
{
  registries {
    id
    name
    tier
  }
}
```

### FederationProof
Cross-registry verification proofs.

**Fields:**
- `id`: Proof ID
- `fromRegistry`: Source registry
- `toRegistry`: Target registry
- `recordHash`: Verified record hash
- `timestamp`: Proof timestamp

## Pagination and Filtering

- Use `first`, `skip` for pagination.
- Use `where` clauses for filtering (e.g., `where: { createdAt_gt: 1640995200 }`).
- Order by timestamp: `orderBy: createdAt, orderDirection: desc`.

## Rate Limits and Access

- Public access with standard GraphQL rate limits.
- For high-volume queries, consider local Graph node or API key (contact team).
- Data is read-only; mutations require on-chain transactions.

## SDKs and Libraries

- **JavaScript**: Use `graphql-request` or Apollo Client.
- **Python**: `gql` library.
- **Integration Examples**: See [Integration Guide](Integration-Guide.md).

→ Next: [Integration Guide](Integration-Guide.md) | Back to [Developer Docs](Developer-Docs.md)