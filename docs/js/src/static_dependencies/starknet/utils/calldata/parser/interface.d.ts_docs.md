# Documentation: js/src/static_dependencies/starknet/utils/calldata/parser/interface.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/parser/interface.d.ts`
- **Size**: 560 bytes
- **Lines**: 21
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi } from '../../../types/index.js';
export declare abstract class AbiParserInterface {
    /**
     * Helper to calculate inputs length from abi
     * @param abiMethod FunctionAbi
     * @return number
     */
    abstract methodInputsLength(abiMethod: FunctionAbi): number;
    /**
     *
     * @param name string
     * @return FunctionAbi | undefined
     */
    abstract getMethod(name: string): FunctionAbi | undefined;
    /**
     * Return Abi in legacy format
     * @return Abi
     */
    abstract getLegacyFormat(): Abi;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/parser/interface.d.ts`.

**Classes defined**: AbiParserInterface

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 20
- Comment lines: 14
- Blank lines: -13

### Main Components

**Classes** (1):
- `AbiParserInterface`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../types/index.js` (imported)
- `../../../types/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/calldata/parser/interface.d.ts
```

