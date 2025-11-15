# Documentation: js/src/static_dependencies/ethers/coders/boolean.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/coders/boolean.d.ts`
- **Size**: 373 bytes
- **Lines**: 13
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
export declare class BooleanCoder extends Coder {
    constructor(localName: string);
    defaultValue(): boolean;
    encode(writer: Writer, _value: boolean | Typed): number;
    decode(reader: Reader): any;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/coders/boolean.d.ts`.

**Classes defined**: BooleanCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 12
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
ts-node js/src/static_dependencies/ethers/coders/boolean.d.ts
```

