# Documentation: js/src/static_dependencies/dydx-v4-client/cosmos/crypto/secp256k1/keys.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/secp256k1/keys.js`
- **Size**: 2,123 bytes
- **Lines**: 72
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
function createBasePubKey() {
    return {
        key: new Uint8Array()
    };
}
export const PubKey = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.key.length !== 0) {
            writer.uint32(10).bytes(message.key);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBasePubKey();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.key = reader.bytes();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBasePubKey();
        message.key = object.key ?? new Uint8Array();
        return message;
    }
};
function createBasePrivKey() {
    return {
        key: new Uint8Array()
    };
}
export const PrivKey = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.key.length !== 0) {
            writer.uint32(10).bytes(message.key);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBasePrivKey();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.key = reader.bytes();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBasePrivKey();
        message.key = object.key ?? new Uint8Array();
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/secp256k1/keys.js`.

**Functions defined**: createBasePrivKey, createBasePubKey

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 71
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `createBasePrivKey()`
- `createBasePubKey()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `protobufjs/minimal.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/dydx-v4-client/cosmos/crypto/secp256k1/keys.js
```

