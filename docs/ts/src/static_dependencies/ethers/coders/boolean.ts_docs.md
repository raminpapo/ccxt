# Documentation: ts/src/static_dependencies/ethers/coders/boolean.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/boolean.ts`
- **Size**: 612 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";

import type { Reader, Writer } from "./abstract-coder.js";

/**
 *  @_ignore
 */
export class BooleanCoder extends Coder {

    constructor(localName: string) {
        super("bool", "bool", localName, false);
    }

    defaultValue(): boolean {
        return false;
    }

    encode(writer: Writer, _value: boolean | Typed): number {
        const value = Typed.dereference(_value, "bool");
        return writer.writeValue(value ? 1: 0);
    }

    decode(reader: Reader): any {
        return !!reader.readValue();
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/boolean.ts`.

**Classes defined**: BooleanCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 21
- Comment lines: 3
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../typed.js` (imported)
- `./abstract-coder.js` (imported)
- `../typed.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/coders/boolean.ts
```

