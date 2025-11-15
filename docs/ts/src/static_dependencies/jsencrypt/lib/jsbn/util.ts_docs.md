# Documentation: ts/src/static_dependencies/jsencrypt/lib/jsbn/util.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/jsencrypt/lib/jsbn/util.ts`
- **Size**: 1,178 bytes
- **Lines**: 70
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
const BI_RM = "0123456789abcdefghijklmnopqrstuvwxyz";

export function int2char(n:number) {
    return BI_RM.charAt(n);
}

//#region BIT_OPERATIONS

// (public) this & a
export function op_and(x:number, y:number):number {
    return x & y;
}


// (public) this | a
export function op_or(x:number, y:number):number {
    return x | y;
}

// (public) this ^ a
export function op_xor(x:number, y:number):number {
    return x ^ y;
}


// (public) this & ~a
export function op_andnot(x:number, y:number):number {
    return x & ~y;
}

// return index of lowest 1-bit in x, x < 2^31
export function lbit(x:number) {
    if (x == 0) {
        return -1;
    }
    let r = 0;
    if ((x & 0xffff) == 0) {
        x >>= 16;
        r += 16;
    }
    if ((x & 0xff) == 0) {
        x >>= 8;
        r += 8;
    }
    if ((x & 0xf) == 0) {
        x >>= 4;
        r += 4;
    }
    if ((x & 3) == 0) {
        x >>= 2;
        r += 2;
    }
    if ((x & 1) == 0) {
        ++r;
    }
    return r;
}

// return number of 1 bits in x
export function cbit(x:number) {
    let r = 0;
    while (x != 0) {
        x &= x - 1;
        ++r;
    }
    return r;
}

//#endregion BIT_OPERATIONS

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/jsencrypt/lib/jsbn/util.ts`.

**Functions defined**: op_or, op_xor, int2char, cbit, op_and, lbit, op_andnot



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 50
- Comment lines: 8
- Blank lines: 12

### Main Components

**Functions** (7):
- `cbit()`
- `int2char()`
- `lbit()`
- `op_and()`
- `op_andnot()`
- `op_or()`
- `op_xor()`

**Constants** (1):
- `BI_RM`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/jsencrypt/lib/jsbn/util.ts
```

