# Integration Guide

This guide walks developers through integrating with Landblock, from basic queries to building DApps. Landblock is designed for incremental adoption — start with read-only access, then add write capabilities.

## Prerequisites

- **Node.js** 18+ or Python 3.8+
- **Web3 Library**: ethers.js, web3.js, or equivalent
- **GraphQL Client**: graphql-request, Apollo, or gql
- **Wallet**: MetaMask or similar for transactions
- **Test MATIC**: Get from Polygon Amoy faucet

## Step 1: Read-Only Integration (Mirror Mode)

Query existing data without deploying contracts.

### Query Spatial Data
```javascript
import { request, gql } from 'graphql-request';

const query = gql`
  {
    spatialUnits(first: 5) {
      id
      boundaryHash
      createdAt
    }
  }
`;

const data = await request('https://api.thegraph.com/subgraphs/name/brockhager/landblock-amoy', query);
console.log(data.spatialUnits);
```

### Verify Proofs
```javascript
// Check if a record hash matches on-chain
const contract = new ethers.Contract(address, abi, provider);
const onChainHash = await contract.getRecordHash(recordId);
const matches = onChainHash === localHash;
```

## Step 2: Identity and Wallets

### Register a DID
```javascript
import { DID } from '@spruceid/didkit';

const did = new DID();
const identity = await did.create();
console.log('DID:', identity.id);
```

### Connect Wallet
```javascript
import { ethers } from 'ethers';

const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();
const address = await signer.getAddress();
```

## Step 3: Write Operations (Verified Mode)

### Submit Evidence
```javascript
// Upload to IPFS, get CID
const cid = await ipfs.add(file);

// Anchor to Landblock
const tx = await contract.submitEvidence(recordId, cid);
await tx.wait();
```

### Record a Transaction
```javascript
// Example: Transfer RRR share
const tx = await rrrContract.transferShare(baUnitId, fromParty, toParty, shareAmount);
await tx.wait();
```

## Step 4: Cross-Registry Federation

### Query Federation Directory
```graphql
{
  registries {
    id
    name
    tier
    endpoint
  }
}
```

### Verify Cross-Registry Proof
```javascript
// Check proof from another registry
const proof = await federationContract.getProof(recordId, sourceRegistry);
const isValid = await federationContract.verifyProof(proof);
```

## Step 5: Building a DApp

### Frontend Setup
```bash
npx create-next-app landblock-dapp
cd landblock-dapp
npm install ethers graphql-request @spruceid/didkit
```

### Sample Component
```jsx
import { useQuery, gql } from '@apollo/client';

const GET_SPATIAL_UNITS = gql`
  query GetSpatialUnits {
    spatialUnits(first: 10) {
      id
      boundaryHash
    }
  }
`;

function SpatialUnitsList() {
  const { loading, error, data } = useQuery(GET_SPATIAL_UNITS);
  
  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;
  
  return (
    <ul>
      {data.spatialUnits.map(unit => (
        <li key={unit.id}>{unit.id}: {unit.boundaryHash}</li>
      ))}
    </ul>
  );
}
```

## Error Handling

- **Network Errors**: Retry with exponential backoff.
- **Gas Estimation**: Use Paymaster for sponsored fees.
- **Validation**: Check tiered disclosure before accessing restricted data.

## Testing

- **Local**: Use Foundry for unit tests.
- **Testnet**: Deploy to Amoy for integration tests.
- **CI/CD**: GitHub Actions with Hardhat/Chai.

## Security Best Practices

- Never store private keys in code.
- Use environment variables for RPC URLs.
- Validate all inputs and outputs.
- Audit contracts before mainnet deployment.

## Resources

- **Docs**: [Contract Addresses](Contract-Addresses.md), [API Reference](API-Reference.md)
- **Examples**: Check private repo for sample code.
- **Support**: Open issues on GitHub or contact team.

→ Next: [Governance Docs](Governance-Docs.md) | Back to [Developer Docs](Developer-Docs.md)