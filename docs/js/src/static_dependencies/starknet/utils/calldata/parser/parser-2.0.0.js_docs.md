# Documentation: js/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.js`
- **Size**: 806 bytes
- **Lines**: 35
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export class AbiParser2 {
    constructor(abi) {
        this.abi = abi;
    }
    /**
     * abi method inputs length
     * @param abiMethod FunctionAbi
     * @returns number
     */
    methodInputsLength(abiMethod) {
        return abiMethod.inputs.length;
    }
    /**
     * get method definition from abi
     * @param name string
     * @returns FunctionAbi | undefined
     */
    getMethod(name) {
        const intf = this.abi.find((it) => it.type === 'interface');
        return intf.items.find((it) => it.name === name);
    }
    /**
     * Get Abi in legacy format
     * @returns Abi
     */
    getLegacyFormat() {
        return this.abi.flatMap((e) => {
            if (e.type === 'interface') {
                return e.items;
            }
            return e;
        });
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.js`.

**Classes defined**: AbiParser2

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 34
- Comment lines: 14
- Blank lines: -13

### Main Components

**Classes** (1):
- `AbiParser2`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/parser/parser-2.0.0.js
```

