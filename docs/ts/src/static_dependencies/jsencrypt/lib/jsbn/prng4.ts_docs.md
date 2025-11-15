# Documentation: ts/src/static_dependencies/jsencrypt/lib/jsbn/prng4.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/jsencrypt/lib/jsbn/prng4.ts`
- **Size**: 1,324 bytes
- **Lines**: 55
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// prng4.js - uses Arcfour as a PRNG

export class Arcfour {
    constructor() {
        this.i = 0;
        this.j = 0;
        this.S = [];
    }

    // Arcfour.prototype.init = ARC4init;
    // Initialize arcfour context from key, an array of ints, each from [0..255]
    public init(key:number[]) {
        let i;
        let j;
        let t;
        for (i = 0; i < 256; ++i) {
            this.S[i] = i;
        }
        j = 0;
        for (i = 0; i < 256; ++i) {
            j = (j + this.S[i] + key[i % key.length]) & 255;
            t = this.S[i];
            this.S[i] = this.S[j];
            this.S[j] = t;
        }
        this.i = 0;
        this.j = 0;
    }

    // Arcfour.prototype.next = ARC4next;
    public next() {
        let t;
        this.i = (this.i + 1) & 255;
        this.j = (this.j + this.S[this.i]) & 255;
        t = this.S[this.i];
        this.S[this.i] = this.S[this.j];
        this.S[this.j] = t;
        return this.S[(t + this.S[this.i]) & 255];
    }

    private i:number;
    private j:number;
    private S:number[];
}


// Plug in your RNG constructor here
export function prng_newstate() {
    return new Arcfour();
}

// Pool size must be a multiple of 4 and greater than 32.
// An array of bytes the size of the pool will be passed to init()
export let rng_psize = 256;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/jsencrypt/lib/jsbn/prng4.ts`.

**Classes defined**: Arcfour

**Functions defined**: prng_newstate



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 40
- Comment lines: 7
- Blank lines: 8

### Main Components

**Classes** (1):
- `Arcfour`

**Functions** (1):
- `prng_newstate()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/jsencrypt/lib/jsbn/prng4.ts
```

