# Documentation: js/src/static_dependencies/ethers/coders/tuple.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/tuple.d.ts`
- **Size**: 474 bytes
- **Lines**: 16
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
export declare class TupleCoder extends Coder {
    readonly coders: ReadonlyArray<Coder>;
    constructor(coders: Array<Coder>, localName: string);
    defaultValue(): any;
    encode(writer: Writer, _value: Array<any> | {
        [name: string]: any;
    } | Typed): number;
    decode(reader: Reader): any;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/coders/tuple.d.ts`.

**Classes defined**: TupleCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 15
- Comment lines: 3
- Blank lines: -2

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
ts-node js/src/static_dependencies/ethers/coders/tuple.d.ts
```

