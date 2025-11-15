# Documentation: js/src/static_dependencies/proxies/agent-base/index.js

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/agent-base/index.js`
- **Size**: 2,901 bytes
- **Lines**: 77
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import * as http from 'http';
export * from './helpers.js';
function isSecureEndpoint() {
    const { stack } = new Error();
    if (typeof stack !== 'string')
        return false;
    return stack
        .split('\n')
        .some((l) => l.indexOf('(https.js:') !== -1 ||
        l.indexOf('node:https:') !== -1);
}
const INTERNAL = Symbol('AgentBaseInternalState');
export class Agent extends http.Agent {
    constructor(opts) {
        super(opts);
        this[INTERNAL] = {};
    }
    createSocket(req, options, cb) {
        // Need to determine whether this is an `http` or `https` request.
        // First check the `secureEndpoint` property explicitly, since this
        // means that a parent `Agent` is "passing through" to this instance.
        let secureEndpoint = typeof options.secureEndpoint === 'boolean'
            ? options.secureEndpoint
            : undefined;
        // If no explicit `secure` endpoint, check if `protocol` property is
        // set. This will usually be the case since using a full string URL
        // or `URL` instance should be the most common case.
        if (typeof secureEndpoint === 'undefined' &&
            typeof options.protocol === 'string') {
            secureEndpoint = options.protocol === 'https:';
        }
        // Finally, if no `protocol` property was set, then fall back to
        // checking the stack trace of the current call stack, and try to
        // detect the "https" module.
        if (typeof secureEndpoint === 'undefined') {
            secureEndpoint = isSecureEndpoint();
        }
        const connectOpts = { ...options, secureEndpoint };
        Promise.resolve()
            .then(() => this.connect(req, connectOpts))
            .then((socket) => {
            if (socket instanceof http.Agent) {
                // @ts-expect-error `addRequest()` isn't defined in `@types/node`
                return socket.addRequest(req, connectOpts);
            }
            this[INTERNAL].currentSocket = socket;
            // @ts-expect-error `createSocket()` isn't defined in `@types/node`
            super.createSocket(req, options, cb);
        }, cb);
    }
    createConnection() {
        const socket = this[INTERNAL].currentSocket;
        this[INTERNAL].currentSocket = undefined;
        if (!socket) {
            throw new Error('No socket was returned in the `connect()` function');
        }
        return socket;
    }
    get defaultPort() {
        return (this[INTERNAL].defaultPort ??
            (this.protocol === 'https:' ? 443 : 80));
    }
    set defaultPort(v) {
        if (this[INTERNAL]) {
            this[INTERNAL].defaultPort = v;
        }
    }
    get protocol() {
        return (this[INTERNAL].protocol ?? (isSecureEndpoint() ? 'https:' : 'http:'));
    }
    set protocol(v) {
        if (this[INTERNAL]) {
            this[INTERNAL].protocol = v;
        }
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/proxies/agent-base/index.js`.

**Classes defined**: Agent

**Functions defined**: isSecureEndpoint

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 77
- Code lines: 65
- Comment lines: 11
- Blank lines: 1

### Main Components

**Functions** (1):
- `isSecureEndpoint()`

**Constants** (1):
- `INTERNAL`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `http` (imported)
- `./helpers.js` (imported)
- `./helpers.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/proxies/agent-base/index.js
```

