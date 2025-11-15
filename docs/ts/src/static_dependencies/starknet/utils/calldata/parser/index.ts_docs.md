# Documentation: ts/src/static_dependencies/starknet/utils/calldata/parser/index.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/parser/index.ts`
- **Size**: 943 bytes
- **Lines**: 32
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Abi, FunctionAbi, RawArgs } from '../../../types/index.js';
import { isCairo1Abi } from '../cairo.js';
import { AbiParserInterface } from './interface.js';
import { AbiParser1 } from './parser-0-1.1.0.js';
import { AbiParser2 } from './parser-2.0.0.js';

export function createAbiParser(abi: Abi): AbiParserInterface {
  const version = getAbiVersion(abi);
  if (version === 0 || version === 1) {
    return new AbiParser1(abi);
  }
  if (version === 2) {
    return new AbiParser2(abi);
  }
  throw Error(`Unsupported ABI version ${version}`);
}

export function getAbiVersion(abi: Abi) {
  if (abi.find((it) => it.type === 'interface')) return 2;
  if (isCairo1Abi(abi)) return 1;
  return 0;
}

export function isNoConstructorValid(
  method: string,
  argsCalldata: RawArgs,
  abiMethod?: FunctionAbi
) {
  // No constructor in abi and validly empty args
  return method === 'constructor' && !abiMethod && !argsCalldata.length;
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/parser/index.ts`.

**Functions defined**: getAbiVersion, createAbiParser, isNoConstructorValid

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 27
- Comment lines: 1
- Blank lines: 4

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
- `../cairo.js` (imported)
- `./parser-2.0.0.js` (imported)
- `./interface.js` (imported)
- `./parser-0-1.1.0.js` (imported)
- `../../../types/index.js` (referenced)
- `../cairo.js` (referenced)
- `./parser-2.0.0.js` (referenced)
- `./interface.js` (referenced)
- `./parser-0-1.1.0.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/utils/calldata/parser/index.ts
```

