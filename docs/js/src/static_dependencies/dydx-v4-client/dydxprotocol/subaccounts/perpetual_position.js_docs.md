# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.js`
- **Size**: 2,137 bytes
- **Lines**: 61
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import * as _m0 from "protobufjs/minimal.js";
function createBasePerpetualPosition() {
    return {
        perpetualId: 0,
        quantums: new Uint8Array(),
        fundingIndex: new Uint8Array(),
        quoteBalance: new Uint8Array()
    };
}
export const PerpetualPosition = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.perpetualId !== 0) {
            writer.uint32(8).uint32(message.perpetualId);
        }
        if (message.quantums.length !== 0) {
            writer.uint32(18).bytes(message.quantums);
        }
        if (message.fundingIndex.length !== 0) {
            writer.uint32(26).bytes(message.fundingIndex);
        }
        if (message.quoteBalance.length !== 0) {
            writer.uint32(34).bytes(message.quoteBalance);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBasePerpetualPosition();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.perpetualId = reader.uint32();
                    break;
                case 2:
                    message.quantums = reader.bytes();
                    break;
                case 3:
                    message.fundingIndex = reader.bytes();
                    break;
                case 4:
                    message.quoteBalance = reader.bytes();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBasePerpetualPosition();
        message.perpetualId = object.perpetualId ?? 0;
        message.quantums = object.quantums ?? new Uint8Array();
        message.fundingIndex = object.fundingIndex ?? new Uint8Array();
        message.quoteBalance = object.quoteBalance ?? new Uint8Array();
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.js`.

**Functions defined**: createBasePerpetualPosition

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 60
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `createBasePerpetualPosition()`



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
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.js
```

