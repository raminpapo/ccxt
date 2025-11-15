# Documentation: ts/src/base/ws/Future.ts

## File Metadata

- **Path**: `ts/src/base/ws/Future.ts`
- **Size**: 1,094 bytes
- **Lines**: 43
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck
import { Unpromise } from "../../static_dependencies/watchable/src/unpromise.js";
export interface FutureInterface extends Promise<any> {
    resolve(value: unknown): void;
    reject(reason?: any): void;
}

export function Future (): FutureInterface {

    let resolve = undefined
        , reject = undefined

    const p = new Promise ((resolve_, reject_) => {
        resolve = resolve_
        reject = reject_
    })

    p.resolve = function _resolve () {
        // eslint-disable-next-line prefer-rest-params
        queueMicrotask (() => {
            resolve.apply (this, arguments)
        })
    }

    p.reject = function _reject () {
        // eslint-disable-next-line prefer-rest-params
        queueMicrotask (() => {
            reject.apply (this, arguments)
        })
    }

    return p
}

function wrapFuture (aggregatePromise): FutureInterface {
    const p = Future ()
    // wrap the promises as a future
    aggregatePromise.then (p.resolve, p.reject)
    return p
}

Future.race = (futures) : FutureInterface => wrapFuture (Unpromise.race (futures))

```

## High-Level Overview

This is a TypeScript file located at `ts/src/base/ws/Future.ts`.

**Functions defined**: _resolve, _reject, wrapFuture, Future

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 30
- Comment lines: 4
- Blank lines: 9

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/base/ws/Future.ts
```

