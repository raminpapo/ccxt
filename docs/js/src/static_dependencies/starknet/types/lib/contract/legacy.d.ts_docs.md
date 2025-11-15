# Documentation: js/src/static_dependencies/starknet/types/lib/contract/legacy.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/lib/contract/legacy.d.ts`
- **Size**: 937 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi } from './abi.js';
/** LEGACY CONTRACT */
/**
 * format produced after compressing 'program' property
 */
export declare type LegacyContractClass = {
    program: CompressedProgram;
    entry_points_by_type: EntryPointsByType;
    abi: Abi;
};
/**
 * format produced after compiling .cairo to .json
 */
export declare type LegacyCompiledContract = Omit<LegacyContractClass, 'program'> & {
    program: Program;
};
/** SUBTYPES */
export declare type Builtins = string[];
export declare type CompressedProgram = string;
export declare type EntryPointsByType = {
    CONSTRUCTOR: ContractEntryPointFields[];
    EXTERNAL: ContractEntryPointFields[];
    L1_HANDLER: ContractEntryPointFields[];
};
export declare type ContractEntryPointFields = {
    selector: string;
    offset: string | number;
    builtins?: Builtins;
};
export interface Program extends Record<string, any> {
    builtins: string[];
    data: string[];
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/lib/contract/legacy.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 33
- Comment lines: 8
- Blank lines: -7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./abi.js` (imported)
- `./abi.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/types/lib/contract/legacy.d.ts
```

