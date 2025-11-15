# Documentation: ts/src/static_dependencies/starknet/types/lib/contract/legacy.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/types/lib/contract/legacy.ts`
- **Size**: 905 bytes
- **Lines**: 41
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi } from './abi.js';

/** LEGACY CONTRACT */
/**
 * format produced after compressing 'program' property
 */
export type LegacyContractClass = {
  program: CompressedProgram;
  entry_points_by_type: EntryPointsByType;
  abi: Abi;
};

/**
 * format produced after compiling .cairo to .json
 */
export type LegacyCompiledContract = Omit<LegacyContractClass, 'program'> & {
  program: Program;
};

/** SUBTYPES */
export type Builtins = string[];
export type CompressedProgram = string;

export type EntryPointsByType = {
  CONSTRUCTOR: ContractEntryPointFields[];
  EXTERNAL: ContractEntryPointFields[];
  L1_HANDLER: ContractEntryPointFields[];
};

export type ContractEntryPointFields = {
  selector: string;
  offset: string | number;
  builtins?: Builtins;
};

export interface Program extends Record<string, any> {
  builtins: string[];
  data: string[];
  // TODO: Add missing properties
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/types/lib/contract/legacy.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 33
- Comment lines: 9
- Blank lines: -1

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
ts-node ts/src/static_dependencies/starknet/types/lib/contract/legacy.ts
```

