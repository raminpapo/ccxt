# Documentation: ts/src/static_dependencies/starknet/utils/calldata/parser/interface.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/parser/interface.ts`
- **Size**: 542 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi } from '../../../types/index.js';

export abstract class AbiParserInterface {
  /**
   * Helper to calculate inputs length from abi
   * @param abiMethod FunctionAbi
   * @return number
   */
  public abstract methodInputsLength(abiMethod: FunctionAbi): number;

  /**
   *
   * @param name string
   * @return FunctionAbi | undefined
   */
  public abstract getMethod(name: string): FunctionAbi | undefined;

  /**
   * Return Abi in legacy format
   * @return Abi
   */
  public abstract getLegacyFormat(): Abi;
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/parser/interface.ts`.

**Classes defined**: AbiParserInterface

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 20
- Comment lines: 14
- Blank lines: -10

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
ts-node ts/src/static_dependencies/starknet/utils/calldata/parser/interface.ts
```

