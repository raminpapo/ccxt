# Documentation: js/src/static_dependencies/dydx-v4-client/google/protobuf/any.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/google/protobuf/any.js`
- **Size**: 1,358 bytes
- **Lines**: 45
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
function createBaseAny() {
    return {
        typeUrl: "",
        value: new Uint8Array()
    };
}
export const Any = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.typeUrl !== "") {
            writer.uint32(10).string(message.typeUrl);
        }
        if (message.value.length !== 0) {
            writer.uint32(18).bytes(message.value);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseAny();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.typeUrl = reader.string();
                    break;
                case 2:
                    message.value = reader.bytes();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseAny();
        message.typeUrl = object.typeUrl ?? "";
        message.value = object.value ?? new Uint8Array();
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/google/protobuf/any.js`.

**Functions defined**: createBaseAny

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 44
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `createBaseAny()`



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
node js/src/static_dependencies/dydx-v4-client/google/protobuf/any.js
```

