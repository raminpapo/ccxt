# Documentation: ts/src/static_dependencies/ethers/coders/fixed-bytes.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/fixed-bytes.ts`
- **Size**: 1,122 bytes
- **Lines**: 38
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import { defineProperties, getBytesCopy, hexlify } from "../utils/index.js";

import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";

import type { BytesLike } from "../utils/index.js";

import type { Reader, Writer } from "./abstract-coder.js";


/**
 *  @_ignore
 */
export class FixedBytesCoder extends Coder {
    readonly size!: number;

    constructor(size: number, localName: string) {
        let name = "bytes" + String(size);
        super(name, name, localName, false);
        defineProperties<FixedBytesCoder>(this, { size }, { size: "number" });
    }

    defaultValue(): string {
        return ("0x0000000000000000000000000000000000000000000000000000000000000000").substring(0, 2 + this.size * 2);
    }

    encode(writer: Writer, _value: BytesLike | Typed): number {
        let data = getBytesCopy(Typed.dereference(_value, this.type));
        if (data.length !== this.size) { this._throwError("incorrect data length", _value); }
        return writer.writeBytes(data);
    }

    decode(reader: Reader): any {
        return hexlify(reader.readBytes(this.size));
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/fixed-bytes.ts`.

**Classes defined**: FixedBytesCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 27
- Comment lines: 3
- Blank lines: 8

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/coders/fixed-bytes.ts
```

