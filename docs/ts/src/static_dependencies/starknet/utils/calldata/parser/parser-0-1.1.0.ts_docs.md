# Documentation: ts/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.ts`
- **Size**: 906 bytes
- **Lines**: 39
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi } from '../../../types/index.js';
import { isLen } from '../cairo.js';
import { AbiParserInterface } from './interface.js';

export class AbiParser1 implements AbiParserInterface {
  abi: Abi;

  constructor(abi: Abi) {
    this.abi = abi;
  }

  /**
   * abi method inputs length without '_len' inputs
   * cairo 0 reducer
   * @param abiMethod FunctionAbi
   * @returns number
   */
  public methodInputsLength(abiMethod: FunctionAbi) {
    return abiMethod.inputs.reduce((acc, input) => (!isLen(input.name) ? acc + 1 : acc), 0);
  }

  /**
   * get method definition from abi
   * @param name string
   * @returns FunctionAbi | undefined
   */
  public getMethod(name: string): FunctionAbi | undefined {
    return this.abi.find((it) => it.name === name);
  }

  /**
   * Get Abi in legacy format
   * @returns Abi
   */
  public getLegacyFormat() {
    return this.abi;
  }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.ts`.

**Classes defined**: AbiParser1

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 33
- Comment lines: 15
- Blank lines: -9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../cairo.js` (imported)
- `../../../types/index.js` (imported)
- `./interface.js` (imported)
- `../cairo.js` (referenced)
- `../../../types/index.js` (referenced)
- `./interface.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.ts
```

