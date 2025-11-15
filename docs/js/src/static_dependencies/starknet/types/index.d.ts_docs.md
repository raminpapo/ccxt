# Documentation: js/src/static_dependencies/starknet/types/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/index.d.ts`
- **Size**: 505 bytes
- **Lines**: 14
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export * from './calldata.js';
export * from './lib/index.js';
export * from './cairoEnum.js';
export declare type ArgsOrCalldata = any;
export declare type Result = any;
export declare type ParsedEvent = any;
export declare type ParsedEvents = any;
export declare type RPC = any;
export declare type InvokeTransactionReceiptResponse = any;
export declare type ContractClassResponse = any;
export declare type FeeEstimate = any;
export declare type UniversalDetails = any;
export * from './typedData.js';

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/index.d.ts`.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 13
- Comment lines: 0
- Blank lines: 1

### Main Components

**Constants** (1):
- `RPC`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./typedData.js` (imported)
- `./cairoEnum.js` (imported)
- `./calldata.js` (imported)
- `./lib/index.js` (imported)
- `./typedData.js` (referenced)
- `./cairoEnum.js` (referenced)
- `./calldata.js` (referenced)
- `./lib/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/types/index.d.ts
```

