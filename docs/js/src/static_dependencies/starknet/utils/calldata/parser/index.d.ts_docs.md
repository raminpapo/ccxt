# Documentation: js/src/static_dependencies/starknet/utils/calldata/parser/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/parser/index.d.ts`
- **Size**: 372 bytes
- **Lines**: 6
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi, RawArgs } from '../../../types/index.js';
import { AbiParserInterface } from './interface.js';
export declare function createAbiParser(abi: Abi): AbiParserInterface;
export declare function getAbiVersion(abi: Abi): 1 | 0 | 2;
export declare function isNoConstructorValid(method: string, argsCalldata: RawArgs, abiMethod?: FunctionAbi): boolean;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/parser/index.d.ts`.

**Functions defined**: getAbiVersion, createAbiParser, isNoConstructorValid

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 6
- Code lines: 5
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (3):
- `createAbiParser()`
- `getAbiVersion()`
- `isNoConstructorValid()`



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
ts-node js/src/static_dependencies/starknet/utils/calldata/parser/index.d.ts
```

