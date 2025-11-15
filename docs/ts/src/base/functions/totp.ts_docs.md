# Documentation: ts/src/base/functions/totp.ts

## File Metadata

- **Path**: `ts/src/base/functions/totp.ts`
- **Size**: 1,093 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { base16, base32 } from '../../static_dependencies/scure-base/index.js';
import { sha1 } from '../../static_dependencies/noble-hashes/sha1.js';
import { hmac } from './crypto.js';

function totp (secret: string) {
    const dec2hex = (s: number) => ((s < 15.5 ? '0' : '') + Math.round (s).toString (16));
    const hex2dec = (s: string) => parseInt (s, 16);
    const leftpad = (s: string, p: string) => (p + s).slice (-p.length); // both s and p are short strings

    secret = secret.replace (' ', ''); // support 2fa-secrets with spaces like "4TDV WOGO" → "4TDVWOGO"
    const epoch = Math.round (new Date ().getTime () / 1000.0);
    const time = leftpad (dec2hex (Math.floor (epoch / 30)), '0000000000000000');
    const hmacRes = hmac (base16.decode (time), base32.decode (secret), sha1, 'hex');
    const offset = hex2dec (hmacRes.substring (hmacRes.length - 1));
    // eslint-disable-next-line
    let otp = (hex2dec (hmacRes.substr (offset * 2, 8)) & hex2dec ('7fffffff')) + '';
    return otp.substring (otp.length - 6, otp.length);
};

export { totp }
export default totp

```

## High-Level Overview

This is a TypeScript file located at `ts/src/base/functions/totp.ts`.

**Functions defined**: totp

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 17
- Comment lines: 1
- Blank lines: 4

### Main Components

**Functions** (1):
- `totp()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../static_dependencies/noble-hashes/sha1.js` (imported)
- `./crypto.js` (imported)
- `../../static_dependencies/scure-base/index.js` (imported)
- `../../static_dependencies/noble-hashes/sha1.js` (referenced)
- `./crypto.js` (referenced)
- `../../static_dependencies/scure-base/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/base/functions/totp.ts
```

