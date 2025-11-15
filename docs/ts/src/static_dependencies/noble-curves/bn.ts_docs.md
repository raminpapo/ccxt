# Documentation: ts/src/static_dependencies/noble-curves/bn.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/noble-curves/bn.ts`
- **Size**: 827 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/*! noble-curves - MIT License (c) 2022 Paul Miller (paulmillr.com) */
import { sha256 } from '../noble-hashes/sha256.js';
import { weierstrass } from './abstract/weierstrass.js';
import { getHash } from './_shortw_utils.js';
import { Fp } from './abstract/modular.js';
/**
 * bn254 pairing-friendly curve.
 * Previously known as alt_bn_128, when it had 128-bit security.
 * Recent research shown it's weaker, the naming has been adjusted to its prime bit count.
 * https://github.com/zcash/zcash/issues/2502
 */
export const bn254 = weierstrass({
  a: BigInt(0),
  b: BigInt(3),
  Fp: Fp(BigInt('0x30644e72e131a029b85045b68181585d97816a916871ca8d3c208c16d87cfd47')),
  n: BigInt('0x30644e72e131a029b85045b68181585d2833e84879b9709143e1f593f0000001'),
  Gx: BigInt(1),
  Gy: BigInt(2),
  h: BigInt(1),
  ...getHash(sha256),
});

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/noble-curves/bn.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 21
- Comment lines: 7
- Blank lines: -6

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./abstract/weierstrass.js` (imported)
- `./_shortw_utils.js` (imported)
- `../noble-hashes/sha256.js` (imported)
- `./abstract/modular.js` (imported)
- `./abstract/weierstrass.js` (referenced)
- `./_shortw_utils.js` (referenced)
- `../noble-hashes/sha256.js` (referenced)
- `./abstract/modular.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/noble-curves/bn.ts
```

