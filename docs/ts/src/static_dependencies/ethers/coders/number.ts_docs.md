# Documentation: ts/src/static_dependencies/ethers/coders/number.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/coders/number.ts`
- **Size**: 1,861 bytes
- **Lines**: 64
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import {
    defineProperties, fromTwos, getBigInt, mask, toTwos
} from "../utils/index.js";

import { Typed } from "../typed.js";
import { Coder, WordSize } from "./abstract-coder.js";

import type { BigNumberish } from "../utils/index.js";

import type { Reader, Writer } from "./abstract-coder.js";


const BN_0 = BigInt(0);
const BN_1 = BigInt(1);
const BN_MAX_UINT256 = BigInt("0xffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff");

/**
 *  @_ignore
 */
export class NumberCoder extends Coder {
    readonly size!: number;
    readonly signed!: boolean;

    constructor(size: number, signed: boolean, localName: string) {
        const name = ((signed ? "int": "uint") + (size * 8));
        super(name, name, localName, false);

        defineProperties<NumberCoder>(this, { size, signed }, { size: "number", signed: "boolean" });
    }

    defaultValue(): number {
        return 0;
    }

    encode(writer: Writer, _value: BigNumberish | Typed): number {
        let value = getBigInt(Typed.dereference(_value, this.type));

        // Check bounds are safe for encoding
        let maxUintValue = mask(BN_MAX_UINT256, WordSize * 8);
        if (this.signed) {
            let bounds = mask(maxUintValue, (this.size * 8) - 1);
            if (value > bounds || value < -(bounds + BN_1)) {
                this._throwError("value out-of-bounds", _value);
            }
            value = toTwos(value, 8 * WordSize);
        } else if (value < BN_0 || value > mask(maxUintValue, this.size * 8)) {
            this._throwError("value out-of-bounds", _value);
        }

        return writer.writeValue(value);
    }

    decode(reader: Reader): any {
        let value = mask(reader.readValue(), this.size * 8);

        if (this.signed) {
            value = fromTwos(value, this.size * 8);
        }

        return value;
    }
}


```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/coders/number.ts`.

**Classes defined**: NumberCoder

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 46
- Comment lines: 4
- Blank lines: 14

### Main Components

**Constants** (3):
- `BN_0`
- `BN_1`
- `BN_MAX_UINT256`



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
ts-node ts/src/static_dependencies/ethers/coders/number.ts
```

