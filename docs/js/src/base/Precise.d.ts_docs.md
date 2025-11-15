# Documentation: js/src/base/Precise.d.ts

## File Metadata

- **Path**: `js/src/base/Precise.d.ts`
- **Size**: 1,683 bytes
- **Lines**: 43
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Str, Int } from './types';
declare class Precise {
    decimals: number;
    integer: bigint;
    base: any;
    constructor(number: bigint | string, decimals?: Int);
    mul(other: Precise): Precise;
    div(other: Precise, precision?: number): Precise;
    add(other: Precise): Precise;
    mod(other: Precise): Precise;
    sub(other: Precise): Precise;
    abs(): Precise;
    neg(): Precise;
    or(other: Precise): Precise;
    min(other: Precise): Precise;
    max(other: Precise): Precise;
    gt(other: Precise): boolean;
    ge(other: Precise): boolean;
    lt(other: Precise): boolean;
    le(other: Precise): boolean;
    reduce(): this;
    equals(other: any): boolean;
    toString(): string;
    static stringMul(string1: Str, string2: Str): string;
    static stringDiv(string1: Str, string2: Str, precision?: number): string;
    static stringAdd(string1: Str, string2: Str): string;
    static stringSub(string1: Str, string2: Str): string;
    static stringAbs(string: Str): string;
    static stringNeg(string: Str): string;
    static stringMod(string1: Str, string2: Str): string;
    static stringOr(string1: Str, string2: Str): string;
    static stringEquals(string1: Str, string2: Str): boolean;
    static stringEq(string1: Str, string2: Str): boolean;
    static stringMin(string1: Str, string2: Str): string;
    static stringMax(string1: Str, string2: Str): string;
    static stringGt(string1: Str, string2: Str): boolean;
    static stringGe(string1: Str, string2: Str): boolean;
    static stringLt(string1: Str, string2: Str): boolean;
    static stringLe(string1: Str, string2: Str): boolean;
}
export default Precise;
export { Precise };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/Precise.d.ts`.

**Classes defined**: Precise

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 42
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `Precise`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./types` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/Precise.d.ts
```

