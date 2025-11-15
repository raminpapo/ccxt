# Documentation: js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.js`
- **Size**: 2,534 bytes
- **Lines**: 80
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
function createBaseMultiSignature() {
    return {
        signatures: []
    };
}
export const MultiSignature = {
    encode(message, writer = _m0.Writer.create()) {
        for (const v of message.signatures) {
            writer.uint32(10).bytes(v);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMultiSignature();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.signatures.push(reader.bytes());
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseMultiSignature();
        message.signatures = object.signatures?.map(e => e) || [];
        return message;
    }
};
function createBaseCompactBitArray() {
    return {
        extraBitsStored: 0,
        elems: new Uint8Array()
    };
}
export const CompactBitArray = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.extraBitsStored !== 0) {
            writer.uint32(8).uint32(message.extraBitsStored);
        }
        if (message.elems.length !== 0) {
            writer.uint32(18).bytes(message.elems);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseCompactBitArray();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.extraBitsStored = reader.uint32();
                    break;
                case 2:
                    message.elems = reader.bytes();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseCompactBitArray();
        message.extraBitsStored = object.extraBitsStored ?? 0;
        message.elems = object.elems ?? new Uint8Array();
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.js`.

**Functions defined**: createBaseCompactBitArray, createBaseMultiSignature

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 79
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `createBaseCompactBitArray()`
- `createBaseMultiSignature()`



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
node js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.js
```

