# Documentation: js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.js`
- **Size**: 736 bytes
- **Lines**: 31
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { isLen } from '../cairo.js';
export class AbiParser1 {
    constructor(abi) {
        this.abi = abi;
    }
    /**
     * abi method inputs length without '_len' inputs
     * cairo 0 reducer
     * @param abiMethod FunctionAbi
     * @returns number
     */
    methodInputsLength(abiMethod) {
        return abiMethod.inputs.reduce((acc, input) => (!isLen(input.name) ? acc + 1 : acc), 0);
    }
    /**
     * get method definition from abi
     * @param name string
     * @returns FunctionAbi | undefined
     */
    getMethod(name) {
        return this.abi.find((it) => it.name === name);
    }
    /**
     * Get Abi in legacy format
     * @returns Abi
     */
    getLegacyFormat() {
        return this.abi;
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.js`.

**Classes defined**: AbiParser1

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 30
- Comment lines: 15
- Blank lines: -14

### Main Components

**Classes** (1):
- `AbiParser1`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../cairo.js` (imported)
- `../cairo.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/parser/parser-0-1.1.0.js
```

