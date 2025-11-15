# Documentation: js/src/static_dependencies/noble-hashes/hkdf.js

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/hkdf.js`
- **Size**: 2,826 bytes
- **Lines**: 72
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from './_assert.js';
import { toBytes } from './utils.js';
import { hmac } from './hmac.js';
// HKDF (RFC 5869)
// https://soatok.blog/2021/11/17/understanding-hkdf/
/**
 * HKDF-Extract(IKM, salt) -> PRK
 * Arguments position differs from spec (IKM is first one, since it is not optional)
 * @param hash
 * @param ikm
 * @param salt
 * @returns
 */
export function extract(hash, ikm, salt) {
    assert.hash(hash);
    // NOTE: some libraries treat zero-length array as 'not provided';
    // we don't, since we have undefined as 'not provided'
    // https://github.com/RustCrypto/KDFs/issues/15
    if (salt === undefined)
        salt = new Uint8Array(hash.outputLen); // if not provided, it is set to a string of HashLen zeros
    return hmac(hash, toBytes(salt), toBytes(ikm));
}
// HKDF-Expand(PRK, info, L) -> OKM
const HKDF_COUNTER = new Uint8Array([0]);
const EMPTY_BUFFER = new Uint8Array();
/**
 * HKDF-expand from the spec.
 * @param prk - a pseudorandom key of at least HashLen octets (usually, the output from the extract step)
 * @param info - optional context and application specific information (can be a zero-length string)
 * @param length - length of output keying material in octets
 */
export function expand(hash, prk, info, length = 32) {
    assert.hash(hash);
    assert.number(length);
    if (length > 255 * hash.outputLen)
        throw new Error('Length should be <= 255*HashLen');
    const blocks = Math.ceil(length / hash.outputLen);
    if (info === undefined)
        info = EMPTY_BUFFER;
    // first L(ength) octets of T
    const okm = new Uint8Array(blocks * hash.outputLen);
    // Re-use HMAC instance between blocks
    const HMAC = hmac.create(hash, prk);
    const HMACTmp = HMAC._cloneInto();
    const T = new Uint8Array(HMAC.outputLen);
    for (let counter = 0; counter < blocks; counter++) {
        HKDF_COUNTER[0] = counter + 1;
        // T(0) = empty string (zero length)
        // T(N) = HMAC-Hash(PRK, T(N-1) | info | N)
        HMACTmp.update(counter === 0 ? EMPTY_BUFFER : T)
            .update(info)
            .update(HKDF_COUNTER)
            .digestInto(T);
        okm.set(T, hash.outputLen * counter);
        HMAC._cloneInto(HMACTmp);
    }
    HMAC.destroy();
    HMACTmp.destroy();
    T.fill(0);
    HKDF_COUNTER.fill(0);
    return okm.slice(0, length);
}
/**
 * HKDF (RFC 5869): extract + expand in one step.
 * @param hash - hash function that would be used (e.g. sha256)
 * @param ikm - input keying material, the initial key
 * @param salt - optional salt value (a non-secret random value)
 * @param info - optional context and application specific information
 * @param length - length of output keying material in octets
 */
export const hkdf = (hash, ikm, salt, info, length) => expand(hash, extract(hash, ikm, salt), info, length);

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/noble-hashes/hkdf.js`.

**Functions defined**: expand, extract, that

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 61
- Comment lines: 32
- Blank lines: -21

### Main Components

**Functions** (3):
- `expand()`
- `extract()`
- `that()`

**Constants** (3):
- `EMPTY_BUFFER`
- `HKDF_COUNTER`
- `HMAC`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./utils.js` (imported)
- `./hmac.js` (imported)
- `./_assert.js` (imported)
- `./utils.js` (referenced)
- `./hmac.js` (referenced)
- `./_assert.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/noble-hashes/hkdf.js
```

