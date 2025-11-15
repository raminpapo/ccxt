# Documentation: ts/src/static_dependencies/starknet/types/index.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/types/index.ts`
- **Size**: 833 bytes
- **Lines**: 25
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export * from './calldata.js';
export * from './lib/index.js';
export * from './cairoEnum.js';

export type ArgsOrCalldata = any;
export type Result = any;
export type ParsedEvent = any;
export type ParsedEvents = any;
export type RPC = any;
export type InvokeTransactionReceiptResponse = any;
export type ContractClassResponse = any;
export type FeeEstimate = any;
// export type TypedDataRevision = any;
// export type StarknetEnumType = any;
// export type StarknetMerkleType = any;
// export type StarknetType = any;
// export type TypedData = any;
export type UniversalDetails = any;
export * from './typedData.js';
// export * from './transactionReceipt.js';
// export * as RPC from './api.js';
// export * from './contract.js';
// export * from './account.js';
// export * from './provider.js';
// export * from './signer.js';
```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/types/index.ts`.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 13
- Comment lines: 11
- Blank lines: 1

### Main Components

**Constants** (1):
- `RPC`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./lib/index.js` (imported)
- `./transactionReceipt.js` (imported)
- `./cairoEnum.js` (imported)
- `./api.js` (imported)
- `./signer.js` (imported)
- `./provider.js` (imported)
- `./typedData.js` (imported)
- `./account.js` (imported)
- `./calldata.js` (imported)
- `./contract.js` (imported)
- `./lib/index.js` (referenced)
- `./transactionReceipt.js` (referenced)
- `./cairoEnum.js` (referenced)
- `./api.js` (referenced)
- `./signer.js` (referenced)
- `./provider.js` (referenced)
- `./typedData.js` (referenced)
- `./account.js` (referenced)
- `./calldata.js` (referenced)
- `./contract.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/types/index.ts
```

