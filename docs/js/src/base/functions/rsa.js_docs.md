# Documentation: js/src/base/functions/rsa.js

## File Metadata

- **Path**: `js/src/base/functions/rsa.js`
- **Size**: 2,361 bytes
- **Lines**: 57
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { JSEncrypt } from "../../static_dependencies/jsencrypt/JSEncrypt.js";
import { base16, utf8 } from '../../static_dependencies/scure-base/index.js';
import { urlencodeBase64, base16ToBinary, base64ToBinary, base64ToBase64Url } from './encode.js';
import { eddsa, hmac } from './crypto.js';
import { P256 } from '../../static_dependencies/noble-curves/p256.js';
import { ecdsa } from '../../base/functions/crypto.js';
import { ed25519 } from "../../static_dependencies/noble-curves/ed25519.js";
function rsa(request, secret, hash) {
    const RSA = new JSEncrypt();
    const digester = (input) => base16.encode(hash(input));
    RSA.setPrivateKey(secret);
    const name = (hash.create()).constructor.name.toLowerCase();
    return RSA.sign(request, digester, name);
}
function jwt(request, secret, hash, isRSA = false, opts = {}) {
    let alg = (isRSA ? 'RS' : 'HS') + (hash.outputLen * 8);
    if (opts['alg']) {
        alg = opts['alg'].toUpperCase();
    }
    const header = Object.assign({ 'alg': alg, 'typ': 'JWT' }, opts);
    if (header['iat'] !== undefined) {
        request['iat'] = header['iat'];
        delete header['iat'];
    }
    const encodedHeader = urlencodeBase64(JSON.stringify(header));
    const encodedData = urlencodeBase64(JSON.stringify(request));
    let token = [encodedHeader, encodedData].join('.');
    const algoType = alg.slice(0, 2);
    let signature = undefined;
    if (algoType === 'HS') {
        signature = urlencodeBase64(hmac(token, secret, hash, 'binary'));
    }
    else if (isRSA || algoType === 'RS') {
        signature = urlencodeBase64(base64ToBinary(rsa(token, utf8.encode(secret), hash)));
    }
    else if (algoType === 'ES') {
        const signedHash = ecdsa(token, utf8.encode(secret), P256, hash);
        const r = signedHash.r.padStart(64, '0');
        const s = signedHash.s.padStart(64, '0');
        signature = urlencodeBase64(base16ToBinary(r + s));
    }
    else if (algoType === 'ED') {
        const base64str = eddsa(toHex(token), secret, ed25519);
        // we need urlencoded64 not base64
        signature = base64ToBase64Url(base64str);
    }
    return [token, signature].join('.');
}
function toHex(str) {
    var result = '';
    for (var i = 0; i < str.length; i++) {
        result += str.charCodeAt(i).toString(16);
    }
    return result;
}
export { rsa, jwt };

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/functions/rsa.js`.

**Functions defined**: toHex, jwt, rsa

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 55
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (3):
- `jwt()`
- `rsa()`
- `toHex()`

**Constants** (1):
- `RSA`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../base/functions/crypto.js` (imported)
- `../../static_dependencies/noble-curves/p256.js` (imported)
- `../../static_dependencies/noble-curves/ed25519.js` (imported)
- `./encode.js` (imported)
- `./crypto.js` (imported)
- `../../static_dependencies/jsencrypt/JSEncrypt.js` (imported)
- `../../static_dependencies/scure-base/index.js` (imported)
- `../../base/functions/crypto.js` (referenced)
- `../../static_dependencies/noble-curves/p256.js` (referenced)
- `../../static_dependencies/noble-curves/ed25519.js` (referenced)
- `./encode.js` (referenced)
- `./crypto.js` (referenced)
- `../../static_dependencies/jsencrypt/JSEncrypt.js` (referenced)
- `../../static_dependencies/scure-base/index.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/functions/rsa.js
```

