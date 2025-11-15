# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/asset_position.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/asset_position.js`
- **Size**: 1,812 bytes
- **Lines**: 54
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { Long } from "../../helpers.js";
import * as _m0 from "protobufjs/minimal.js";
function createBaseAssetPosition() {
    return {
        assetId: 0,
        quantums: new Uint8Array(),
        index: Long.UZERO
    };
}
export const AssetPosition = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.assetId !== 0) {
            writer.uint32(8).uint32(message.assetId);
        }
        if (message.quantums.length !== 0) {
            writer.uint32(18).bytes(message.quantums);
        }
        if (!message.index.isZero()) {
            writer.uint32(24).uint64(message.index);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseAssetPosition();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.assetId = reader.uint32();
                    break;
                case 2:
                    message.quantums = reader.bytes();
                    break;
                case 3:
                    message.index = reader.uint64();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseAssetPosition();
        message.assetId = object.assetId ?? 0;
        message.quantums = object.quantums ?? new Uint8Array();
        message.index = object.index !== undefined && object.index !== null ? Long.fromValue(object.index) : Long.UZERO;
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/asset_position.js`.

**Functions defined**: createBaseAssetPosition

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 53
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `createBaseAssetPosition()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `../../helpers.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `../../helpers.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/asset_position.js
```

