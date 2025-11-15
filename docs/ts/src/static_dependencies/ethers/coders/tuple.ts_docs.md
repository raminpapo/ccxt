# Documentation: ts/src/static_dependencies/ethers/coders/tuple.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/tuple.ts`
- **Size**: 2,052 bytes
- **Lines**: 70
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { defineProperties } from "../utils/properties.js";

import { Typed } from "../typed.js";
import { Coder } from "./abstract-coder.js";

import { pack, unpack } from "./array.js";

import type { Reader, Writer } from "./abstract-coder.js";

/**
 *  @_ignore
 */
export class TupleCoder extends Coder {
    readonly coders!: ReadonlyArray<Coder>;

    constructor(coders: Array<Coder>, localName: string) {
        let dynamic = false;
        const types: Array<string> = [];
        coders.forEach((coder) => {
            if (coder.dynamic) { dynamic = true; }
            types.push(coder.type);
        });
        const type = ("tuple(" + types.join(",") + ")");

        super("tuple", type, localName, dynamic);
        defineProperties<TupleCoder>(this, { coders: Object.freeze(coders.slice()) });
    }

    defaultValue(): any {
        const values: any = [ ];
        this.coders.forEach((coder) => {
            values.push(coder.defaultValue());
        });

        // We only output named properties for uniquely named coders
        const uniqueNames = this.coders.reduce((accum, coder) => {
            const name = coder.localName;
            if (name) {
                if (!accum[name]) { accum[name] = 0; }
                accum[name]++;
            }
            return accum;
        }, <{ [ name: string ]: number }>{ });

        // Add named values
        this.coders.forEach((coder: Coder, index: number) => {
            let name = coder.localName;
            if (!name || uniqueNames[name] !== 1) { return; }

            if (name === "length") { name = "_length"; }

            if (values[name] != null) { return; }

            values[name] = values[index];
        });

        return Object.freeze(values);
    }

    encode(writer: Writer, _value: Array<any> | { [ name: string ]: any } | Typed): number {
        const value = Typed.dereference(_value, "tuple");
        return pack(writer, this.coders, value);
    }

    decode(reader: Reader): any {
        return unpack(reader, this.coders);
    }
}


```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/tuple.ts`.

**Classes defined**: TupleCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 51
- Comment lines: 5
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./array.js` (imported)
- `../utils/properties.js` (imported)
- `../typed.js` (imported)
- `./abstract-coder.js` (imported)
- `./array.js` (referenced)
- `../utils/properties.js` (referenced)
- `../typed.js` (referenced)
- `./abstract-coder.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/coders/tuple.ts
```

