# Documentation: ts/src/static_dependencies/ethers/coders/address.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/address.ts`
- **Size**: 922 bytes
- **Lines**: 37
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { getAddress } from "../address/index.js";
import { toBeHex } from "../utils/maths.js";

import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";

import type { Reader, Writer } from "./abstract-coder.js";


/**
 *  @_ignore
 */
export class AddressCoder extends Coder {

    constructor(localName: string) {
        super("address", "address", localName, false);
    }

    defaultValue(): string {
        return "0x0000000000000000000000000000000000000000";
    }

    encode(writer: Writer, _value: string | Typed): number {
        let value = Typed.dereference(_value, "string");
        try {
            value = getAddress(value);
        } catch (error: any) {
            return this._throwError(error.message, _value);
        }
        return writer.writeValue(value);
    }

    decode(reader: Reader): any {
        return getAddress(toBeHex(reader.readValue(), 20));
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/address.ts`.

**Classes defined**: AddressCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 28
- Comment lines: 3
- Blank lines: 6

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/coders/address.ts
```

