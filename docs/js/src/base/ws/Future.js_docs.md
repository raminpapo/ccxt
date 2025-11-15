# Documentation: js/src/base/ws/Future.js

## File Metadata

- **Path**: `js/src/base/ws/Future.js`
- **Size**: 902 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// @ts-nocheck
import { Unpromise } from "../../static_dependencies/watchable/src/unpromise.js";
export function Future() {
    let resolve = undefined, reject = undefined;
    const p = new Promise((resolve_, reject_) => {
        resolve = resolve_;
        reject = reject_;
    });
    p.resolve = function _resolve() {
        // eslint-disable-next-line prefer-rest-params
        queueMicrotask(() => {
            resolve.apply(this, arguments);
        });
    };
    p.reject = function _reject() {
        // eslint-disable-next-line prefer-rest-params
        queueMicrotask(() => {
            reject.apply(this, arguments);
        });
    };
    return p;
}
function wrapFuture(aggregatePromise) {
    const p = Future();
    // wrap the promises as a future
    aggregatePromise.then(p.resolve, p.reject);
    return p;
}
Future.race = (futures) => wrapFuture(Unpromise.race(futures));

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/ws/Future.js`.

**Functions defined**: _resolve, _reject, wrapFuture, Future

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 25
- Comment lines: 4
- Blank lines: 1

### Main Components

**Functions** (4):
- `Future()`
- `_reject()`
- `_resolve()`
- `wrapFuture()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../static_dependencies/watchable/src/unpromise.js` (imported)
- `../../static_dependencies/watchable/src/unpromise.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/ws/Future.js
```

