# Documentation: js/src/static_dependencies/ethers/coders/array.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/array.d.ts`
- **Size**: 734 bytes
- **Lines**: 25
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Typed } from "../typed.js";
import { Coder, Result, Writer } from "./abstract-coder.js";
import type { Reader } from "./abstract-coder.js";
/**
 *  @_ignore
 */
export declare function pack(writer: Writer, coders: ReadonlyArray<Coder>, values: Array<any> | {
    [name: string]: any;
}): number;
/**
 *  @_ignore
 */
export declare function unpack(reader: Reader, coders: ReadonlyArray<Coder>): Result;
/**
 *  @_ignore
 */
export declare class ArrayCoder extends Coder {
    readonly coder: Coder;
    readonly length: number;
    constructor(coder: Coder, length: number, localName: string);
    defaultValue(): Array<any>;
    encode(writer: Writer, _value: Array<any> | Typed): number;
    decode(reader: Reader): any;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/coders/array.d.ts`.

**Classes defined**: ArrayCoder

**Functions defined**: pack, unpack

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 24
- Comment lines: 9
- Blank lines: -8

### Main Components

**Functions** (2):
- `pack()`
- `unpack()`



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
ts-node js/src/static_dependencies/ethers/coders/array.d.ts
```

