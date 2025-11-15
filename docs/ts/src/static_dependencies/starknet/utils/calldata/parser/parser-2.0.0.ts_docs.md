# Documentation: ts/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.ts`
- **Size**: 1,114 bytes
- **Lines**: 45
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi, EventAbi, StructAbi, InterfaceAbi } from '../../../types/index.js';
import { AbiParserInterface } from './interface.js';

export class AbiParser2 implements AbiParserInterface {
  abi: Abi;

  constructor(abi: Abi) {
    this.abi = abi;
  }

  /**
   * abi method inputs length
   * @param abiMethod FunctionAbi
   * @returns number
   */
  public methodInputsLength(abiMethod: FunctionAbi) {
    return abiMethod.inputs.length;
  }

  /**
   * get method definition from abi
   * @param name string
   * @returns FunctionAbi | undefined
   */
  public getMethod(name: string): FunctionAbi | undefined {
    const intf = this.abi.find(
      (it: FunctionAbi | EventAbi | StructAbi | InterfaceAbi) => it.type === 'interface'
    ) as InterfaceAbi;
    return intf.items.find((it) => it.name === name);
  }

  /**
   * Get Abi in legacy format
   * @returns Abi
   */
  public getLegacyFormat(): Abi {
    return this.abi.flatMap((e: FunctionAbi | EventAbi | StructAbi | InterfaceAbi) => {
      if (e.type === 'interface') {
        return e.items;
      }
      return e;
    });
  }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.ts`.

**Classes defined**: AbiParser2

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 39
- Comment lines: 14
- Blank lines: -8

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
ts-node ts/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.ts
```

