# Documentation: js/src/static_dependencies/ethers/coders/tuple.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/tuple.js`
- **Size**: 1,898 bytes
- **Lines**: 62
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { defineProperties } from "../utils/properties.js";
import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";
import { pack, unpack } from "./array.js";
/**
 *  @_ignore
 */
export class TupleCoder extends Coder {
    constructor(coders, localName) {
        let dynamic = false;
        const types = [];
        coders.forEach((coder) => {
            if (coder.dynamic) {
                dynamic = true;
            }
            types.push(coder.type);
        });
        const type = ("tuple(" + types.join(",") + ")");
        super("tuple", type, localName, dynamic);
        defineProperties(this, { coders: Object.freeze(coders.slice()) });
    }
    defaultValue() {
        const values = [];
        this.coders.forEach((coder) => {
            values.push(coder.defaultValue());
        });
        // We only output named properties for uniquely named coders
        const uniqueNames = this.coders.reduce((accum, coder) => {
            const name = coder.localName;
            if (name) {
                if (!accum[name]) {
                    accum[name] = 0;
                }
                accum[name]++;
            }
            return accum;
        }, {});
        // Add named values
        this.coders.forEach((coder, index) => {
            let name = coder.localName;
            if (!name || uniqueNames[name] !== 1) {
                return;
            }
            if (name === "length") {
                name = "_length";
            }
            if (values[name] != null) {
                return;
            }
            values[name] = values[index];
        });
        return Object.freeze(values);
    }
    encode(writer, _value) {
        const value = Typed.dereference(_value, "tuple");
        return pack(writer, this.coders, value);
    }
    decode(reader) {
        return unpack(reader, this.coders);
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/coders/tuple.js`.

**Classes defined**: TupleCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 59
- Comment lines: 5
- Blank lines: -2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./array.js` (imported)
- `../utils/properties.js` (imported)
- `../typed.js` (imported)
- `./abstract-coder.js` (imported)
- `./array.js` (referenced)
- `../utils/properties.js` (referenced)
- `../typed.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/coders/tuple.js
```

