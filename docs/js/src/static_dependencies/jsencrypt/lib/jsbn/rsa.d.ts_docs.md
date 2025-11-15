# Documentation: js/src/static_dependencies/jsencrypt/lib/jsbn/rsa.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/jsencrypt/lib/jsbn/rsa.d.ts`
- **Size**: 990 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BigInteger } from "./jsbn.js";
export declare class RSAKey {
    constructor();
    doPublic(x: BigInteger): BigInteger;
    doPrivate(x: BigInteger): BigInteger;
    setPublic(N: string, E: string): void;
    encrypt(text: string): string;
    setPrivate(N: string, E: string, D: string): void;
    setPrivateEx(N: string, E: string, D: string, P: string, Q: string, DP: string, DQ: string, C: string): void;
    generate(B: number, E: string): void;
    decrypt(ctext: string): string;
    generateAsync(B: number, E: string, callback: () => void): void;
    sign(text: string, digestMethod: (str: string) => string, digestName: string): string;
    verify(text: string, signature: string, digestMethod: (str: string) => string): boolean;
    protected n: BigInteger;
    protected e: number;
    protected d: BigInteger;
    protected p: BigInteger;
    protected q: BigInteger;
    protected dmp1: BigInteger;
    protected dmq1: BigInteger;
    protected coeff: BigInteger;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/jsencrypt/lib/jsbn/rsa.d.ts`.

**Classes defined**: RSAKey

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 23
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `RSAKey`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./jsbn.js` (imported)
- `./jsbn.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/jsencrypt/lib/jsbn/rsa.d.ts
```

