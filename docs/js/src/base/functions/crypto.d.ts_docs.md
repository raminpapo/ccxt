# Documentation: js/src/base/functions/crypto.d.ts

## File Metadata

- **Path**: `js/src/base/functions/crypto.d.ts`
- **Size**: 1,003 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { CHash, Input } from '../../static_dependencies/noble-hashes/utils.js';
import { CurveFn } from '../../static_dependencies/noble-curves/abstract/weierstrass.js';
import { CurveFn as CurveFnEDDSA } from '../../static_dependencies/noble-curves/abstract/edwards.js';
import { Hex } from '../../static_dependencies/noble-curves/abstract/utils.js';
declare type Digest = 'binary' | 'hex' | 'base64';
declare const hash: (request: Input, hash: CHash, digest?: Digest) => any;
declare const hmac: (request: Input, secret: Input, hash: CHash, digest?: Digest) => any;
declare function ecdsa(request: Hex, secret: Hex, curve: CurveFn, prehash?: CHash, fixedLength?: boolean): {
    r: string;
    s: string;
    v: number;
};
declare function axolotl(request: Hex, secret: Hex, curve: CurveFnEDDSA): string;
declare function eddsa(request: Hex, secret: Input, curve: CurveFnEDDSA): string;
declare function crc32(str: any, signed?: boolean): number;
export { hash, hmac, crc32, ecdsa, eddsa, axolotl, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/crypto.d.ts`.

**Functions defined**: ecdsa, crc32, axolotl, eddsa

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 16
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (4):
- `axolotl()`
- `crc32()`
- `ecdsa()`
- `eddsa()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../static_dependencies/noble-curves/abstract/edwards.js` (imported)
- `../../static_dependencies/noble-hashes/utils.js` (imported)
- `../../static_dependencies/noble-curves/abstract/utils.js` (imported)
- `../../static_dependencies/noble-curves/abstract/weierstrass.js` (imported)
- `../../static_dependencies/noble-curves/abstract/edwards.js` (referenced)
- `../../static_dependencies/noble-hashes/utils.js` (referenced)
- `../../static_dependencies/noble-curves/abstract/utils.js` (referenced)
- `../../static_dependencies/noble-curves/abstract/weierstrass.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/crypto.d.ts
```

