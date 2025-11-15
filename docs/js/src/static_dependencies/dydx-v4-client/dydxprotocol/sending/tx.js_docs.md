# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.js`
- **Size**: 4,661 bytes
- **Lines**: 142
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { Transfer } from "./transfer.js";
import _m0 from "protobufjs/minimal.js";
function createBaseMsgCreateTransfer() {
    return {
        transfer: undefined
    };
}
export const MsgCreateTransfer = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.transfer !== undefined) {
            Transfer.encode(message.transfer, writer.uint32(10).fork()).ldelim();
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMsgCreateTransfer();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.transfer = Transfer.decode(reader, reader.uint32());
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseMsgCreateTransfer();
        message.transfer = object.transfer !== undefined && object.transfer !== null ? Transfer.fromPartial(object.transfer) : undefined;
        return message;
    }
};
function createBaseMsgCreateTransferResponse() {
    return {};
}
export const MsgCreateTransferResponse = {
    encode(_, writer = _m0.Writer.create()) {
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMsgCreateTransferResponse();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(_) {
        const message = createBaseMsgCreateTransferResponse();
        return message;
    }
};
function createBaseMsgDepositToSubaccountResponse() {
    return {};
}
export const MsgDepositToSubaccountResponse = {
    encode(_, writer = _m0.Writer.create()) {
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMsgDepositToSubaccountResponse();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(_) {
        const message = createBaseMsgDepositToSubaccountResponse();
        return message;
    }
};
function createBaseMsgWithdrawFromSubaccountResponse() {
    return {};
}
export const MsgWithdrawFromSubaccountResponse = {
    encode(_, writer = _m0.Writer.create()) {
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMsgWithdrawFromSubaccountResponse();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(_) {
        const message = createBaseMsgWithdrawFromSubaccountResponse();
        return message;
    }
};
function createBaseMsgSendFromModuleToAccountResponse() {
    return {};
}
export const MsgSendFromModuleToAccountResponse = {
    encode(_, writer = _m0.Writer.create()) {
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMsgSendFromModuleToAccountResponse();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(_) {
        const message = createBaseMsgSendFromModuleToAccountResponse();
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.js`.

**Functions defined**: createBaseMsgCreateTransfer, createBaseMsgWithdrawFromSubaccountResponse, createBaseMsgCreateTransferResponse, createBaseMsgDepositToSubaccountResponse, createBaseMsgSendFromModuleToAccountResponse

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 142
- Code lines: 141
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (5):
- `createBaseMsgCreateTransfer()`
- `createBaseMsgCreateTransferResponse()`
- `createBaseMsgDepositToSubaccountResponse()`
- `createBaseMsgSendFromModuleToAccountResponse()`
- `createBaseMsgWithdrawFromSubaccountResponse()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./transfer.js` (imported)
- `protobufjs/minimal.js` (imported)
- `./transfer.js` (referenced)
- `protobufjs/minimal.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.js
```

