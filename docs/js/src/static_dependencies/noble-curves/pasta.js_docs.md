# Documentation: js/src/static_dependencies/noble-curves/pasta.js

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/pasta.js`
- **Size**: 942 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/*! noble-curves - MIT License (c) 2022 Paul Miller (paulmillr.com) */
import { sha256 } from '../noble-hashes/sha256.js';
import { weierstrass } from './abstract/weierstrass.js';
import { getHash } from './_shortw_utils.js';
import * as mod from './abstract/modular.js';
export const p = BigInt('0x40000000000000000000000000000000224698fc094cf91b992d30ed00000001');
export const q = BigInt('0x40000000000000000000000000000000224698fc0994a8dd8c46eb2100000001');
// https://neuromancer.sk/std/other/Pallas
export const pallas = weierstrass({
    a: BigInt(0),
    b: BigInt(5),
    Fp: mod.Fp(p),
    n: q,
    Gx: mod.mod(BigInt(-1), p),
    Gy: BigInt(2),
    h: BigInt(1),
    ...getHash(sha256),
});
// https://neuromancer.sk/std/other/Vesta
export const vesta = weierstrass({
    a: BigInt(0),
    b: BigInt(5),
    Fp: mod.Fp(q),
    n: p,
    Gx: mod.mod(BigInt(-1), q),
    Gy: BigInt(2),
    h: BigInt(1),
    ...getHash(sha256),
});

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/noble-curves/pasta.js`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 27
- Comment lines: 3
- Blank lines: 0

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

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/noble-curves/pasta.js
```

