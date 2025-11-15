# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations_config.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations_config.js`
- **Size**: 8,106 bytes
- **Lines**: 191
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
import { Long } from "../../helpers.js";
function createBaseLiquidationsConfig() {
    return {
        maxLiquidationFeePpm: 0,
        positionBlockLimits: undefined,
        subaccountBlockLimits: undefined,
        fillablePriceConfig: undefined
    };
}
export const LiquidationsConfig = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.maxLiquidationFeePpm !== 0) {
            writer.uint32(8).uint32(message.maxLiquidationFeePpm);
        }
        if (message.positionBlockLimits !== undefined) {
            PositionBlockLimits.encode(message.positionBlockLimits, writer.uint32(18).fork()).ldelim();
        }
        if (message.subaccountBlockLimits !== undefined) {
            SubaccountBlockLimits.encode(message.subaccountBlockLimits, writer.uint32(26).fork()).ldelim();
        }
        if (message.fillablePriceConfig !== undefined) {
            FillablePriceConfig.encode(message.fillablePriceConfig, writer.uint32(34).fork()).ldelim();
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseLiquidationsConfig();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.maxLiquidationFeePpm = reader.uint32();
                    break;
                case 2:
                    message.positionBlockLimits = PositionBlockLimits.decode(reader, reader.uint32());
                    break;
                case 3:
                    message.subaccountBlockLimits = SubaccountBlockLimits.decode(reader, reader.uint32());
                    break;
                case 4:
                    message.fillablePriceConfig = FillablePriceConfig.decode(reader, reader.uint32());
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseLiquidationsConfig();
        message.maxLiquidationFeePpm = object.maxLiquidationFeePpm ?? 0;
        message.positionBlockLimits = object.positionBlockLimits !== undefined && object.positionBlockLimits !== null ? PositionBlockLimits.fromPartial(object.positionBlockLimits) : undefined;
        message.subaccountBlockLimits = object.subaccountBlockLimits !== undefined && object.subaccountBlockLimits !== null ? SubaccountBlockLimits.fromPartial(object.subaccountBlockLimits) : undefined;
        message.fillablePriceConfig = object.fillablePriceConfig !== undefined && object.fillablePriceConfig !== null ? FillablePriceConfig.fromPartial(object.fillablePriceConfig) : undefined;
        return message;
    }
};
function createBasePositionBlockLimits() {
    return {
        minPositionNotionalLiquidated: Long.UZERO,
        maxPositionPortionLiquidatedPpm: 0
    };
}
export const PositionBlockLimits = {
    encode(message, writer = _m0.Writer.create()) {
        if (!message.minPositionNotionalLiquidated.isZero()) {
            writer.uint32(8).uint64(message.minPositionNotionalLiquidated);
        }
        if (message.maxPositionPortionLiquidatedPpm !== 0) {
            writer.uint32(16).uint32(message.maxPositionPortionLiquidatedPpm);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBasePositionBlockLimits();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.minPositionNotionalLiquidated = reader.uint64();
                    break;
                case 2:
                    message.maxPositionPortionLiquidatedPpm = reader.uint32();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBasePositionBlockLimits();
        message.minPositionNotionalLiquidated = object.minPositionNotionalLiquidated !== undefined && object.minPositionNotionalLiquidated !== null ? Long.fromValue(object.minPositionNotionalLiquidated) : Long.UZERO;
        message.maxPositionPortionLiquidatedPpm = object.maxPositionPortionLiquidatedPpm ?? 0;
        return message;
    }
};
function createBaseSubaccountBlockLimits() {
    return {
        maxNotionalLiquidated: Long.UZERO,
        maxQuantumsInsuranceLost: Long.UZERO
    };
}
export const SubaccountBlockLimits = {
    encode(message, writer = _m0.Writer.create()) {
        if (!message.maxNotionalLiquidated.isZero()) {
            writer.uint32(8).uint64(message.maxNotionalLiquidated);
        }
        if (!message.maxQuantumsInsuranceLost.isZero()) {
            writer.uint32(16).uint64(message.maxQuantumsInsuranceLost);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseSubaccountBlockLimits();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.maxNotionalLiquidated = reader.uint64();
                    break;
                case 2:
                    message.maxQuantumsInsuranceLost = reader.uint64();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseSubaccountBlockLimits();
        message.maxNotionalLiquidated = object.maxNotionalLiquidated !== undefined && object.maxNotionalLiquidated !== null ? Long.fromValue(object.maxNotionalLiquidated) : Long.UZERO;
        message.maxQuantumsInsuranceLost = object.maxQuantumsInsuranceLost !== undefined && object.maxQuantumsInsuranceLost !== null ? Long.fromValue(object.maxQuantumsInsuranceLost) : Long.UZERO;
        return message;
    }
};
function createBaseFillablePriceConfig() {
    return {
        bankruptcyAdjustmentPpm: 0,
        spreadToMaintenanceMarginRatioPpm: 0
    };
}
export const FillablePriceConfig = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.bankruptcyAdjustmentPpm !== 0) {
            writer.uint32(8).uint32(message.bankruptcyAdjustmentPpm);
        }
        if (message.spreadToMaintenanceMarginRatioPpm !== 0) {
            writer.uint32(16).uint32(message.spreadToMaintenanceMarginRatioPpm);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseFillablePriceConfig();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.bankruptcyAdjustmentPpm = reader.uint32();
                    break;
                case 2:
                    message.spreadToMaintenanceMarginRatioPpm = reader.uint32();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseFillablePriceConfig();
        message.bankruptcyAdjustmentPpm = object.bankruptcyAdjustmentPpm ?? 0;
        message.spreadToMaintenanceMarginRatioPpm = object.spreadToMaintenanceMarginRatioPpm ?? 0;
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations_config.js`.

**Functions defined**: createBaseFillablePriceConfig, createBaseSubaccountBlockLimits, createBaseLiquidationsConfig, createBasePositionBlockLimits

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 191
- Code lines: 190
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (4):
- `createBaseFillablePriceConfig()`
- `createBaseLiquidationsConfig()`
- `createBasePositionBlockLimits()`
- `createBaseSubaccountBlockLimits()`



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
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/liquidations_config.js
```

