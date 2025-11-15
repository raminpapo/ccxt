# Documentation: js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.js`
- **Size**: 1,538 bytes
- **Lines**: 46
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { Any } from "../../../google/protobuf/any.js";
import _m0 from "protobufjs/minimal.js";
function createBaseLegacyAminoPubKey() {
    return {
        threshold: 0,
        publicKeys: []
    };
}
export const LegacyAminoPubKey = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.threshold !== 0) {
            writer.uint32(8).uint32(message.threshold);
        }
        for (const v of message.publicKeys) {
            Any.encode(v, writer.uint32(18).fork()).ldelim();
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseLegacyAminoPubKey();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.threshold = reader.uint32();
                    break;
                case 2:
                    message.publicKeys.push(Any.decode(reader, reader.uint32()));
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseLegacyAminoPubKey();
        message.threshold = object.threshold ?? 0;
        message.publicKeys = object.publicKeys?.map(e => Any.fromPartial(e)) || [];
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.js`.

**Functions defined**: createBaseLegacyAminoPubKey

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 45
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `createBaseLegacyAminoPubKey()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `../../../google/protobuf/any.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `../../../google/protobuf/any.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.js
```

