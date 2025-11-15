# Documentation: js/src/static_dependencies/ethers/coders/fixed-bytes.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/fixed-bytes.js`
- **Size**: 904 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { defineProperties, getBytesCopy, hexlify } from "../utils/index.js";
import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";
/**
 *  @_ignore
 */
export class FixedBytesCoder extends Coder {
    constructor(size, localName) {
        let name = "bytes" + String(size);
        super(name, name, localName, false);
        defineProperties(this, { size }, { size: "number" });
    }
    defaultValue() {
        return ("0x0000000000000000000000000000000000000000000000000000000000000000").substring(0, 2 + this.size * 2);
    }
    encode(writer, _value) {
        let data = getBytesCopy(Typed.dereference(_value, this.type));
        if (data.length !== this.size) {
            this._throwError("incorrect data length", _value);
        }
        return writer.writeBytes(data);
    }
    decode(reader) {
        return hexlify(reader.readBytes(this.size));
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/coders/fixed-bytes.js`.

**Classes defined**: FixedBytesCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
- Comment lines: 3
- Blank lines: -2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../typed.js` (imported)
- `../utils/index.js` (imported)
- `./abstract-coder.js` (imported)
- `../typed.js` (referenced)
- `../utils/index.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/coders/fixed-bytes.js
```

