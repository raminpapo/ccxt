# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.js`
- **Size**: 4,373 bytes
- **Lines**: 104
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import _m0 from "protobufjs/minimal.js";
function createBaseBlockRateLimitConfiguration() {
    return {
        maxShortTermOrdersPerNBlocks: [],
        maxStatefulOrdersPerNBlocks: [],
        maxShortTermOrderCancellationsPerNBlocks: [],
        maxShortTermOrdersAndCancelsPerNBlocks: []
    };
}
export const BlockRateLimitConfiguration = {
    encode(message, writer = _m0.Writer.create()) {
        for (const v of message.maxShortTermOrdersPerNBlocks) {
            MaxPerNBlocksRateLimit.encode(v, writer.uint32(10).fork()).ldelim();
        }
        for (const v of message.maxStatefulOrdersPerNBlocks) {
            MaxPerNBlocksRateLimit.encode(v, writer.uint32(18).fork()).ldelim();
        }
        for (const v of message.maxShortTermOrderCancellationsPerNBlocks) {
            MaxPerNBlocksRateLimit.encode(v, writer.uint32(26).fork()).ldelim();
        }
        for (const v of message.maxShortTermOrdersAndCancelsPerNBlocks) {
            MaxPerNBlocksRateLimit.encode(v, writer.uint32(34).fork()).ldelim();
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseBlockRateLimitConfiguration();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.maxShortTermOrdersPerNBlocks.push(MaxPerNBlocksRateLimit.decode(reader, reader.uint32()));
                    break;
                case 2:
                    message.maxStatefulOrdersPerNBlocks.push(MaxPerNBlocksRateLimit.decode(reader, reader.uint32()));
                    break;
                case 3:
                    message.maxShortTermOrderCancellationsPerNBlocks.push(MaxPerNBlocksRateLimit.decode(reader, reader.uint32()));
                    break;
                case 4:
                    message.maxShortTermOrdersAndCancelsPerNBlocks.push(MaxPerNBlocksRateLimit.decode(reader, reader.uint32()));
                    break;
                default:
                    reader.skipType(tag & 7);
                    break;
            }
        }
        return message;
    },
    fromPartial(object) {
        const message = createBaseBlockRateLimitConfiguration();
        message.maxShortTermOrdersPerNBlocks = object.maxShortTermOrdersPerNBlocks?.map(e => MaxPerNBlocksRateLimit.fromPartial(e)) || [];
        message.maxStatefulOrdersPerNBlocks = object.maxStatefulOrdersPerNBlocks?.map(e => MaxPerNBlocksRateLimit.fromPartial(e)) || [];
        message.maxShortTermOrderCancellationsPerNBlocks = object.maxShortTermOrderCancellationsPerNBlocks?.map(e => MaxPerNBlocksRateLimit.fromPartial(e)) || [];
        message.maxShortTermOrdersAndCancelsPerNBlocks = object.maxShortTermOrdersAndCancelsPerNBlocks?.map(e => MaxPerNBlocksRateLimit.fromPartial(e)) || [];
        return message;
    }
};
function createBaseMaxPerNBlocksRateLimit() {
    return {
        numBlocks: 0,
        limit: 0
    };
}
export const MaxPerNBlocksRateLimit = {
    encode(message, writer = _m0.Writer.create()) {
        if (message.numBlocks !== 0) {
            writer.uint32(8).uint32(message.numBlocks);
        }
        if (message.limit !== 0) {
            writer.uint32(16).uint32(message.limit);
        }
        return writer;
    },
    decode(input, length) {
        const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
        let end = length === undefined ? reader.len : reader.pos + length;
        const message = createBaseMaxPerNBlocksRateLimit();
        while (reader.pos < end) {
            const tag = reader.uint32();
            switch (tag >>> 3) {
                case 1:
                    message.numBlocks = reader.uint32();
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
        const message = createBaseMaxPerNBlocksRateLimit();
        message.numBlocks = object.numBlocks ?? 0;
        message.limit = object.limit ?? 0;
        return message;
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.js`.

**Functions defined**: createBaseBlockRateLimitConfiguration, createBaseMaxPerNBlocksRateLimit

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 104
- Code lines: 103
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `createBaseBlockRateLimitConfiguration()`
- `createBaseMaxPerNBlocksRateLimit()`



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
node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.js
```

