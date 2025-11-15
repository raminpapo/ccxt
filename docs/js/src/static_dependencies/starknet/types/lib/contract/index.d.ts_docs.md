# Documentation: js/src/static_dependencies/starknet/types/lib/contract/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/lib/contract/index.d.ts`
- **Size**: 801 bytes
- **Lines**: 25
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { LegacyCompiledContract, LegacyContractClass } from './legacy.js';
import { CompiledSierra, SierraContractClass } from './sierra.js';
/**
 * format produced after compressing compiled contract
 *
 * CompressedCompiledContract
 */
export declare type ContractClass = LegacyContractClass | SierraContractClass;
/**
 * format produced after compile .cairo to .json
 */
export declare type CompiledContract = LegacyCompiledContract | CompiledSierra;
/**
 * Compressed or decompressed Cairo0 or Cairo1 Contract
 */
export declare type CairoContract = ContractClass | CompiledContract;
export declare enum EntryPointType {
    EXTERNAL = "EXTERNAL",
    L1_HANDLER = "L1_HANDLER",
    CONSTRUCTOR = "CONSTRUCTOR"
}
export * from './abi.js';
export * from './legacy.js';
export * from './sierra.js';

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/lib/contract/index.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 24
- Comment lines: 11
- Blank lines: -10

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
ts-node js/src/static_dependencies/starknet/types/lib/contract/index.d.ts
```

