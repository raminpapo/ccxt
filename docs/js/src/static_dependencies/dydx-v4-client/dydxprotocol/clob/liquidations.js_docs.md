# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations.js`
- **Size**: 6,342 bytes
- **Lines**: 159
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { SubaccountId } from "../subaccounts/subaccount.js";
import * as _m0 from "protobufjs/minimal.js";
import { Long } from "../../helpers.js";
function createBasePerpetualLiquidationInfo() {
    return {
        subaccountId: undefined,
        perpetualId: 0
    };
}
export const PerpetualLiquidationInfo = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.subaccountId !== undefined) {
            SubaccountId.encode(message.subaccountId, writer.uint32(10).fork()).ldelim();
        }
        if (message.perpetualId !== 0) {
            writer.uint32(16).uint32(message.perpetualId);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBasePerpetualLiquidationInfo();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.subaccountId = SubaccountId.decode(reader, reader.uint32());
                    break;
                case 2:
                    message.perpetualId = reader.uint32();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBasePerpetualLiquidationInfo();
        message.subaccountId = object.subaccountId !== undefined && object.subaccountId !== null ? SubaccountId.fromPartial(object.subaccountId) : undefined;
        message.perpetualId = object.perpetualId ?? 0;
        return message;
    }
};
function createBaseSubaccountLiquidationInfo() {
    return {
        perpetualsLiquidated: [],
        notionalLiquidated: Long.UZERO,
        quantumsInsuranceLost: Long.UZERO
    };
}
export const SubaccountLiquidationInfo = {
    encode(message, writer = _m0.Writer.create()) {
        writer.uint32(10).fork();
        for (const v of message.perpetualsLiquidated) {
            writer.uint32(v);
        }
        writer.ldelim();
        if (!message.notionalLiquidated.isZero()) {
            writer.uint32(16).uint64(message.notionalLiquidated);
        }
        if (!message.quantumsInsuranceLost.isZero()) {
            writer.uint32(24).uint64(message.quantumsInsuranceLost);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseSubaccountLiquidationInfo();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    if ((tag & 7) === 2) {
                        const end2 = reader.uint32() + reader.pos;
                        while (reader.pos < end2) {
                            message.perpetualsLiquidated.push(reader.uint32());
                        }
                    }
                    else {
                        message.perpetualsLiquidated.push(reader.uint32());
                    }
                    break;
                case 2:
                    message.notionalLiquidated = reader.uint64();
                    break;
                case 3:
                    message.quantumsInsuranceLost = reader.uint64();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseSubaccountLiquidationInfo();
        message.perpetualsLiquidated = object.perpetualsLiquidated?.map(e => e) || [];
        message.notionalLiquidated = object.notionalLiquidated !== undefined && object.notionalLiquidated !== null ? Long.fromValue(object.notionalLiquidated) : Long.UZERO;
        message.quantumsInsuranceLost = object.quantumsInsuranceLost !== undefined && object.quantumsInsuranceLost !== null ? Long.fromValue(object.quantumsInsuranceLost) : Long.UZERO;
        return message;
    }
};
function createBaseSubaccountOpenPositionInfo() {
    return {
        perpetualId: 0,
        subaccountsWithLongPosition: [],
        subaccountsWithShortPosition: []
    };
}
export const SubaccountOpenPositionInfo = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.perpetualId !== 0) {
            writer.uint32(8).uint32(message.perpetualId);
        }
        for (const v of message.subaccountsWithLongPosition) {
            SubaccountId.encode(v, writer.uint32(18).fork()).ldelim();
        }
        for (const v of message.subaccountsWithShortPosition) {
            SubaccountId.encode(v, writer.uint32(26).fork()).ldelim();
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseSubaccountOpenPositionInfo();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.perpetualId = reader.uint32();
                    break;
                case 2:
                    message.subaccountsWithLongPosition.push(SubaccountId.decode(reader, reader.uint32()));
                    break;
                case 3:
                    message.subaccountsWithShortPosition.push(SubaccountId.decode(reader, reader.uint32()));
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseSubaccountOpenPositionInfo();
        message.perpetualId = object.perpetualId ?? 0;
        message.subaccountsWithLongPosition = object.subaccountsWithLongPosition?.map(e => SubaccountId.fromPartial(e)) || [];
        message.subaccountsWithShortPosition = object.subaccountsWithShortPosition?.map(e => SubaccountId.fromPartial(e)) || [];
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations.js`.

**Functions defined**: createBaseSubaccountLiquidationInfo, createBaseSubaccountOpenPositionInfo, createBasePerpetualLiquidationInfo

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 159
- Code lines: 158
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (3):
- `createBasePerpetualLiquidationInfo()`
- `createBaseSubaccountLiquidationInfo()`
- `createBaseSubaccountOpenPositionInfo()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `../subaccounts/subaccount.js` (imported)
- `../../helpers.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `../subaccounts/subaccount.js` (referenced)
- `../../helpers.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations.js
```

