# Documentation: js/src/static_dependencies/starknet/types/lib/contract/sierra.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/lib/contract/sierra.d.ts`
- **Size**: 1,660 bytes
- **Lines**: 53
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi } from './abi.js';
import { EntryPointsByType } from './legacy.js';
/** SYSTEM TYPES */
export declare type CairoAssembly = {
    prime: string;
    compiler_version: string;
    bytecode: ByteCode;
    hints: any[];
    pythonic_hints?: PythonicHints;
    bytecode_segment_lengths?: number[];
    entry_points_by_type: EntryPointsByType;
};
/** COMPILED CONTRACT */
/**
 * format produced after starknet-compile .cairo to .json
 *
 * sierra_program is hex array
 */
export declare type CompiledSierra = {
    sierra_program: ByteCode;
    sierra_program_debug_info?: SierraProgramDebugInfo;
    contract_class_version: string;
    entry_points_by_type: SierraEntryPointsByType;
    abi: Abi;
};
/**
 * format produced after compressing 'sierra_program', stringifies 'abi' property and omit sierra_program_debug_info
 *
 * CompressedCompiledSierra
 */
export declare type SierraContractClass = Omit<CompiledSierra, 'abi' | 'sierra_program_debug_info'> & {
    sierra_program: string;
    abi: string;
};
export declare type CompiledSierraCasm = CairoAssembly;
/** SUBTYPES */
export declare type ByteCode = string[];
export declare type PythonicHints = [number, string[]][];
export declare type SierraProgramDebugInfo = {
    type_names: [number, string][];
    libfunc_names: [number, string][];
    user_func_names: [number, string][];
};
export declare type SierraEntryPointsByType = {
    CONSTRUCTOR: SierraContractEntryPointFields[];
    EXTERNAL: SierraContractEntryPointFields[];
    L1_HANDLER: SierraContractEntryPointFields[];
};
export declare type SierraContractEntryPointFields = {
    selector: string;
    function_idx: number;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/lib/contract/sierra.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 52
- Comment lines: 13
- Blank lines: -12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./legacy.js` (imported)
- `./abi.js` (imported)
- `./legacy.js` (referenced)
- `./abi.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/types/lib/contract/sierra.d.ts
```

