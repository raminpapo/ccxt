# Documentation: ts/src/static_dependencies/ethers/coders/bytes.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/bytes.ts`
- **Size**: 949 bytes
- **Lines**: 44
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { getBytesCopy, hexlify } from "../utils/index.js";

import { Coder } from "./abstract-coder.js";

import type { Reader, Writer } from "./abstract-coder.js";


/**
 *  @_ignore
 */
export class DynamicBytesCoder extends Coder {
    constructor(type: string, localName: string) {
       super(type, type, localName, true);
    }

    defaultValue(): string {
        return "0x";
    }

    encode(writer: Writer, value: any): number {
        value = getBytesCopy(value);
        let length = writer.writeValue(value.length);
        length += writer.writeBytes(value);
        return length;
    }

    decode(reader: Reader): any {
        return reader.readBytes(reader.readIndex(), true);
    }
}

/**
 *  @_ignore
 */
export class BytesCoder extends DynamicBytesCoder {
    constructor(localName: string) {
        super("bytes", localName);
    }

    decode(reader: Reader): any {
        return hexlify(super.decode(reader));
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/bytes.ts`.

**Classes defined**: DynamicBytesCoder, BytesCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 34
- Comment lines: 6
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../utils/index.js` (imported)
- `./abstract-coder.js` (imported)
- `../utils/index.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/coders/bytes.ts
```

