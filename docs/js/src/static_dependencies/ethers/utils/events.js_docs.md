# Documentation: js/src/static_dependencies/ethers/utils/events.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/events.js`
- **Size**: 2,288 bytes
- **Lines**: 47
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
var __classPrivateFieldSet = (this && this.__classPrivateFieldSet) || function (receiver, state, value, kind, f) {
    if (kind === "m") throw new TypeError("Private method is not writable");
    if (kind === "a" && !f) throw new TypeError("Private accessor was defined without a setter");
    if (typeof state === "function" ? receiver !== state || !f : !state.has(receiver)) throw new TypeError("Cannot write private member to an object whose class did not declare it");
    return (kind === "a" ? f.call(receiver, value) : f ? f.value = value : state.set(receiver, value)), value;
};
var __classPrivateFieldGet = (this && this.__classPrivateFieldGet) || function (receiver, state, kind, f) {
    if (kind === "a" && !f) throw new TypeError("Private accessor was defined without a getter");
    if (typeof state === "function" ? receiver !== state || !f : !state.has(receiver)) throw new TypeError("Cannot read private member from an object whose class did not declare it");
    return kind === "m" ? f : kind === "a" ? f.call(receiver) : f ? f.value : state.get(receiver);
};
var _EventPayload_listener;
/**
 *  Events allow for applications to use the observer pattern, which
 *  allows subscribing and publishing events, outside the normal
 *  execution paths.
 *
 *  @_section api/utils/events:Events  [about-events]
 */
import { defineProperties } from "./properties.js";
/**
 *  When an [[EventEmitterable]] triggers a [[Listener]], the
 *  callback always ahas one additional argument passed, which is
 *  an **EventPayload**.
 */
export class EventPayload {
    /**
     *  Create a new **EventPayload** for %%emitter%% with
     *  the %%listener%% and for %%filter%%.
     */
    constructor(emitter, listener, filter) {
        _EventPayload_listener.set(this, void 0);
        __classPrivateFieldSet(this, _EventPayload_listener, listener, "f");
        defineProperties(this, { emitter, filter });
    }
    /**
     *  Unregister the triggered listener for future events.
     */
    async removeListener() {
        if (__classPrivateFieldGet(this, _EventPayload_listener, "f") == null) {
            return;
        }
        await this.emitter.off(this.filter, __classPrivateFieldGet(this, _EventPayload_listener, "f"));
    }
}
_EventPayload_listener = new WeakMap();

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/utils/events.js`.

**Classes defined**: EventPayload, did

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 46
- Comment lines: 19
- Blank lines: -18

### Main Components

**Classes** (1):
- `EventPayload`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./properties.js` (imported)
- `./properties.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/utils/events.js
```

