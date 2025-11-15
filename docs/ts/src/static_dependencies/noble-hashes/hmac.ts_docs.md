# Documentation: ts/src/static_dependencies/noble-hashes/hmac.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/noble-hashes/hmac.ts`
- **Size**: 2,690 bytes
- **Lines**: 82
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from './_assert.js';
import { Hash, CHash, Input, toBytes } from './utils.js';
// HMAC (RFC 2104)
class HMAC<T extends Hash<T>> extends Hash<HMAC<T>> {
  oHash: T;
  iHash: T;
  blockLen: number;
  outputLen: number;
  private finished = false;
  private destroyed = false;

  constructor(hash: CHash, _key: Input) {
    super();
    assert.hash(hash);
    const key = toBytes(_key);
    this.iHash = hash.create() as T;
    if (typeof this.iHash.update !== 'function')
      throw new TypeError('Expected instance of class which extends utils.Hash');
    this.blockLen = this.iHash.blockLen;
    this.outputLen = this.iHash.outputLen;
    const blockLen = this.blockLen;
    const pad = new Uint8Array(blockLen);
    // blockLen can be bigger than outputLen
    pad.set(key.length > blockLen ? hash.create().update(key).digest() : key);
    for (let i = 0; i < pad.length; i++) pad[i] ^= 0x36;
    this.iHash.update(pad);
    // By doing update (processing of first block) of outer hash here we can re-use it between multiple calls via clone
    this.oHash = hash.create() as T;
    // Undo internal XOR && apply outer XOR
    for (let i = 0; i < pad.length; i++) pad[i] ^= 0x36 ^ 0x5c;
    this.oHash.update(pad);
    pad.fill(0);
  }
  update(buf: Input) {
    assert.exists(this);
    this.iHash.update(buf);
    return this;
  }
  digestInto(out: Uint8Array) {
    assert.exists(this);
    assert.bytes(out, this.outputLen);
    this.finished = true;
    this.iHash.digestInto(out);
    this.oHash.update(out);
    this.oHash.digestInto(out);
    this.destroy();
  }
  digest() {
    const out = new Uint8Array(this.oHash.outputLen);
    this.digestInto(out);
    return out;
  }
  _cloneInto(to?: HMAC<T>): HMAC<T> {
    // Create new instance without calling constructor since key already in state and we don't know it.
    to ||= Object.create(Object.getPrototypeOf(this), {});
    const { oHash, iHash, finished, destroyed, blockLen, outputLen } = this;
    to = to as this;
    to.finished = finished;
    to.destroyed = destroyed;
    to.blockLen = blockLen;
    to.outputLen = outputLen;
    to.oHash = oHash._cloneInto(to.oHash);
    to.iHash = iHash._cloneInto(to.iHash);
    return to;
  }
  destroy() {
    this.destroyed = true;
    this.oHash.destroy();
    this.iHash.destroy();
  }
}

/**
 * HMAC: RFC2104 message authentication code.
 * @param hash - function that would be used e.g. sha256
 * @param key - message key
 * @param message - message data
 */
export const hmac = (hash: CHash, key: Input, message: Input): Uint8Array =>
  new HMAC<any>(hash, key).update(message).digest();
hmac.create = (hash: CHash, key: Input) => new HMAC<any>(hash, key);

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/noble-hashes/hmac.ts`.

**Classes defined**: which, HMAC

**Functions defined**: that

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 82
- Code lines: 74
- Comment lines: 11
- Blank lines: -3

### Main Components

**Functions** (1):
- `that()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./utils.js` (imported)
- `./_assert.js` (imported)
- `./utils.js` (referenced)
- `./_assert.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/noble-hashes/hmac.ts
```

