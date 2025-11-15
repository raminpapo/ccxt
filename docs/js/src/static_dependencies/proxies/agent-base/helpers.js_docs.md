# Documentation: js/src/static_dependencies/proxies/agent-base/helpers.js

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/agent-base/helpers.js`
- **Size**: 1,043 bytes
- **Lines**: 37
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import * as http from 'http';
import * as https from 'https';
export async function toBuffer(stream) {
    let length = 0;
    const chunks = [];
    for await (const chunk of stream) {
        length += chunk.length;
        chunks.push(chunk);
    }
    return Buffer.concat(chunks, length);
}
// eslint-disable-next-line @typescript-eslint/no-explicit-any
export async function json(stream) {
    const buf = await toBuffer(stream);
    const str = buf.toString('utf8');
    try {
        return JSON.parse(str);
    }
    catch (_err) {
        const err = _err;
        err.message += ` (input: ${str})`;
        throw err;
    }
}
export function req(url, opts = {}) {
    const href = typeof url === 'string' ? url : url.href;
    const req = (href.startsWith('https:') ? https : http).request(url, opts);
    const promise = new Promise((resolve, reject) => {
        req
            .once('response', resolve)
            .once('error', reject)
            .end();
    });
    req.then = promise.then.bind(promise);
    return req;
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/proxies/agent-base/helpers.js`.

**Functions defined**: toBuffer, json, req

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 35
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (3):
- `json()`
- `req()`
- `toBuffer()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `https` (imported)
- `http` (imported)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/proxies/agent-base/helpers.js
```

