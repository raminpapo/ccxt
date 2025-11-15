# Documentation: ts/src/static_dependencies/ethers/coders/null.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/null.ts`
- **Size**: 603 bytes
- **Lines**: 29
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Coder } from "./abstract-coder.js";
import type { Reader, Writer } from "./abstract-coder.js";

const Empty = new Uint8Array([ ]);

/**
 *  @_ignore
 */
export class NullCoder extends Coder {

    constructor(localName: string) {
        super("null", "", localName, false);
    }

    defaultValue(): null {
        return null;
    }

    encode(writer: Writer, value: any): number {
        if (value != null) { this._throwError("not null", value); }
        return writer.writeBytes(Empty);
    }

    decode(reader: Reader): any {
        reader.readBytes(0);
        return null;
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/null.ts`.

**Classes defined**: NullCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 22
- Comment lines: 3
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./abstract-coder.js` (imported)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/coders/null.ts
```

