# Documentation: js/src/base/functions/rsa.d.ts

## File Metadata

- **Path**: `js/src/base/functions/rsa.d.ts`
- **Size**: 342 bytes
- **Lines**: 6
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { CHash } from '../../static_dependencies/noble-hashes/utils.js';
import { Dictionary } from "../types.js";
declare function rsa(request: string, secret: string, hash: CHash): string;
declare function jwt(request: Dictionary<any>, secret: Uint8Array, hash: CHash, isRSA?: boolean, opts?: Dictionary<any>): string;
export { rsa, jwt };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/rsa.d.ts`.

**Functions defined**: jwt, rsa

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 6
- Code lines: 5
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `jwt()`
- `rsa()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../static_dependencies/noble-hashes/utils.js` (imported)
- `../types.js` (imported)
- `../../static_dependencies/noble-hashes/utils.js` (referenced)
- `../types.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/rsa.d.ts
```

