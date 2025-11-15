# Documentation: js/src/static_dependencies/ethers/coders/address.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/address.js`
- **Size**: 797 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { getAddress } from "../address/index.js";
import { toBeHex } from "../utils/maths.js";
import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";
/**
 *  @_ignore
 */
export class AddressCoder extends Coder {
    constructor(localName) {
        super("address", "address", localName, false);
    }
    defaultValue() {
        return "0x0000000000000000000000000000000000000000";
    }
    encode(writer, _value) {
        let value = Typed.dereference(_value, "string");
        try {
            value = getAddress(value);
        }
        catch (error) {
            return this._throwError(error.message, _value);
        }
        return writer.writeValue(value);
    }
    decode(reader) {
        return getAddress(toBeHex(reader.readValue(), 20));
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/coders/address.js`.

**Classes defined**: AddressCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 28
- Comment lines: 3
- Blank lines: -2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../utils/maths.js` (imported)
- `../typed.js` (imported)
- `../address/index.js` (imported)
- `./abstract-coder.js` (imported)
- `../utils/maths.js` (referenced)
- `../typed.js` (referenced)
- `../address/index.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/coders/address.js
```

