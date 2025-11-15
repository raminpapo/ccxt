# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.js`
- **Size**: 3,221 bytes
- **Lines**: 88
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
function createBaseEquityTierLimitConfiguration() {
    return {
        shortTermOrderEquityTiers: [],
        statefulOrderEquityTiers: []
    };
}
export const EquityTierLimitConfiguration = {
    encode(message, writer = _m0.Writer.create()) {
        for (const v of message.shortTermOrderEquityTiers) {
            EquityTierLimit.encode(v, writer.uint32(10).fork()).ldelim();
        }
        for (const v of message.statefulOrderEquityTiers) {
            EquityTierLimit.encode(v, writer.uint32(18).fork()).ldelim();
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseEquityTierLimitConfiguration();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.shortTermOrderEquityTiers.push(EquityTierLimit.decode(reader, reader.uint32()));
                    break;
                case 2:
                    message.statefulOrderEquityTiers.push(EquityTierLimit.decode(reader, reader.uint32()));
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseEquityTierLimitConfiguration();
        message.shortTermOrderEquityTiers = object.shortTermOrderEquityTiers?.map(e => EquityTierLimit.fromPartial(e)) || [];
        message.statefulOrderEquityTiers = object.statefulOrderEquityTiers?.map(e => EquityTierLimit.fromPartial(e)) || [];
        return message;
    }
};
function createBaseEquityTierLimit() {
    return {
        usdTncRequired: new Uint8Array(),
        limit: 0
    };
}
export const EquityTierLimit = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.usdTncRequired.length !== 0) {
            writer.uint32(10).bytes(message.usdTncRequired);
        }
        if (message.limit !== 0) {
            writer.uint32(16).uint32(message.limit);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseEquityTierLimit();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.usdTncRequired = reader.bytes();
                    break;
                case 2:
                    message.limit = reader.uint32();
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseEquityTierLimit();
        message.usdTncRequired = object.usdTncRequired ?? new Uint8Array();
        message.limit = object.limit ?? 0;
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.js`.

**Functions defined**: createBaseEquityTierLimitConfiguration, createBaseEquityTierLimit

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 88
- Code lines: 87
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `createBaseEquityTierLimit()`
- `createBaseEquityTierLimitConfiguration()`



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
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.js
```

