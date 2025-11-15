# Documentation: ts/src/static_dependencies/starknet/types/lib/contract/index.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/types/lib/contract/index.ts`
- **Size**: 802 bytes
- **Lines**: 32
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { LegacyCompiledContract, LegacyContractClass } from './legacy.js';
import { CompiledSierra, SierraContractClass } from './sierra.js';

// Final types
/**
 * format produced after compressing compiled contract
 *
 * CompressedCompiledContract
 */
export type ContractClass = LegacyContractClass | SierraContractClass;

/**
 * format produced after compile .cairo to .json
 */
export type CompiledContract = LegacyCompiledContract | CompiledSierra;

/**
 * Compressed or decompressed Cairo0 or Cairo1 Contract
 */
export type CairoContract = ContractClass | CompiledContract;

// Basic elements
export enum EntryPointType {
  EXTERNAL = 'EXTERNAL',
  L1_HANDLER = 'L1_HANDLER',
  CONSTRUCTOR = 'CONSTRUCTOR',
}

export * from './abi.js';
export * from './legacy.js';
export * from './sierra.js';

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/types/lib/contract/index.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 24
- Comment lines: 13
- Blank lines: -5

### Main Components

**Constants** (3):
- `CONSTRUCTOR`
- `EXTERNAL`
- `L1_HANDLER`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./legacy.js` (imported)
- `./sierra.js` (imported)
- `./abi.js` (imported)
- `./legacy.js` (referenced)
- `./sierra.js` (referenced)
- `./abi.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/types/lib/contract/index.ts
```

