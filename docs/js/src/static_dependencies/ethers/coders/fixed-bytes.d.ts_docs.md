# Documentation: js/src/static_dependencies/ethers/coders/fixed-bytes.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/fixed-bytes.d.ts`
- **Size**: 470 bytes
- **Lines**: 15
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";
import type { BytesLike } from "../utils/index.js";
import type { Reader, Writer } from "./abstract-coder.js";
/**
 *  @_ignore
 */
export declare class FixedBytesCoder extends Coder {
    readonly size: number;
    constructor(size: number, localName: string);
    defaultValue(): string;
    encode(writer: Writer, _value: BytesLike | Typed): number;
    decode(reader: Reader): any;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/coders/fixed-bytes.d.ts`.

**Classes defined**: FixedBytesCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 14
- Comment lines: 3
- Blank lines: -2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../utils/index.js` (imported)
- `../typed.js` (imported)
- `./abstract-coder.js` (imported)
- `../utils/index.js` (referenced)
- `../typed.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/coders/fixed-bytes.d.ts
```

