# Documentation: js/src/static_dependencies/starknet/utils/calldata/parser/index.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/parser/index.js`
- **Size**: 795 bytes
- **Lines**: 25
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { isCairo1Abi } from '../cairo.js';
import { AbiParser1 } from './parser-0-1.1.0.js';
import { AbiParser2 } from './parser-2.0.0.js';
export function createAbiParser(abi) {
    const version = getAbiVersion(abi);
    if (version === 0 || version === 1) {
        return new AbiParser1(abi);
    }
    if (version === 2) {
        return new AbiParser2(abi);
    }
    throw Error(`Unsupported ABI version ${version}`);
}
export function getAbiVersion(abi) {
    if (abi.find((it) => it.type === 'interface'))
        return 2;
    if (isCairo1Abi(abi))
        return 1;
    return 0;
}
export function isNoConstructorValid(method, argsCalldata, abiMethod) {
    // No constructor in abi and validly empty args
    return method === 'constructor' && !abiMethod && !argsCalldata.length;
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/parser/index.js`.

**Functions defined**: getAbiVersion, createAbiParser, isNoConstructorValid

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 23
- Comment lines: 1
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

- `./parser-2.0.0.js` (imported)
- `../cairo.js` (imported)
- `./parser-0-1.1.0.js` (imported)
- `./parser-2.0.0.js` (referenced)
- `../cairo.js` (referenced)
- `./parser-0-1.1.0.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/parser/index.js
```

