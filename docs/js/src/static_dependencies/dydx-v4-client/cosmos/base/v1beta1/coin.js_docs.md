# Documentation: js/src/static_dependencies/dydx-v4-client/cosmos/base/v1beta1/coin.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/cosmos/base/v1beta1/coin.js`
- **Size**: 4,649 bytes
- **Lines**: 158
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
function createBaseCoin() {
    return {
        denom: "",
        amount: ""
    };
}
export const Coin = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.denom !== "") {
            writer.uint32(10).string(message.denom);
        }
        if (message.amount !== "") {
            writer.uint32(18).string(message.amount);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseCoin();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.denom = reader.string();
                    break;
                case 2:
                    message.amount = reader.string();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseCoin();
        message.denom = object.denom ?? "";
        message.amount = object.amount ?? "";
        return message;
    }
};
function createBaseDecCoin() {
    return {
        denom: "",
        amount: ""
    };
}
export const DecCoin = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.denom !== "") {
            writer.uint32(10).string(message.denom);
        }
        if (message.amount !== "") {
            writer.uint32(18).string(message.amount);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseDecCoin();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.denom = reader.string();
                    break;
                case 2:
                    message.amount = reader.string();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseDecCoin();
        message.denom = object.denom ?? "";
        message.amount = object.amount ?? "";
        return message;
    }
};
function createBaseIntProto() {
    return {
        int: ""
    };
}
export const IntProto = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.int !== "") {
            writer.uint32(10).string(message.int);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseIntProto();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.int = reader.string();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseIntProto();
        message.int = object.int ?? "";
        return message;
    }
};
function createBaseDecProto() {
    return {
        dec: ""
    };
}
export const DecProto = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.dec !== "") {
            writer.uint32(10).string(message.dec);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseDecProto();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.dec = reader.string();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseDecProto();
        message.dec = object.dec ?? "";
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/cosmos/base/v1beta1/coin.js`.

**Functions defined**: createBaseDecCoin, createBaseCoin, createBaseDecProto, createBaseIntProto

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 158
- Code lines: 157
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (4):
- `createBaseCoin()`
- `createBaseDecCoin()`
- `createBaseDecProto()`
- `createBaseIntProto()`



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
node js/src/static_dependencies/dydx-v4-client/cosmos/base/v1beta1/coin.js
```

