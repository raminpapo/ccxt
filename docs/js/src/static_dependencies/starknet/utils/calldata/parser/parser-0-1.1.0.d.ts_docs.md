# Documentation: js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.d.ts`
- **Size**: 698 bytes
- **Lines**: 25
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi } from '../../../types/index.js';
import { AbiParserInterface } from './interface.js';
export declare class AbiParser1 implements AbiParserInterface {
    abi: Abi;
    constructor(abi: Abi);
    /**
     * abi method inputs length without '_len' inputs
     * cairo 0 reducer
     * @param abiMethod FunctionAbi
     * @returns number
     */
    methodInputsLength(abiMethod: FunctionAbi): number;
    /**
     * get method definition from abi
     * @param name string
     * @returns FunctionAbi | undefined
     */
    getMethod(name: string): FunctionAbi | undefined;
    /**
     * Get Abi in legacy format
     * @returns Abi
     */
    getLegacyFormat(): Abi;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.d.ts`.

**Classes defined**: AbiParser1

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 24
- Comment lines: 15
- Blank lines: -14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../types/index.js` (imported)
- `./interface.js` (imported)
- `../../../types/index.js` (referenced)
- `./interface.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.d.ts
```

