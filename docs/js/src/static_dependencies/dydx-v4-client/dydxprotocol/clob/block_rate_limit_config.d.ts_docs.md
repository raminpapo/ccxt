# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.d.ts`
- **Size**: 2,871 bytes
- **Lines**: 67
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../helpers.js";
/** Defines the block rate limits for CLOB specific operations. */
export interface BlockRateLimitConfiguration {
    /**
     * How many short term order attempts (successful and failed) are allowed for
     * an account per N blocks. Note that the rate limits are applied
     * in an AND fashion such that an order placement must pass all rate limit
     * configurations.
     *
     * Specifying 0 values disables this rate limit.
     * Deprecated in favor of `max_short_term_orders_and_cancels_per_n_blocks`
     * for v5.x onwards.
     */
    /** @deprecated */
    maxShortTermOrdersPerNBlocks: MaxPerNBlocksRateLimit[];
    /**
     * How many stateful order attempts (successful and failed) are allowed for
     * an account per N blocks. Note that the rate limits are applied
     * in an AND fashion such that an order placement must pass all rate limit
     * configurations.
     *
     * Specifying 0 values disables this rate limit.
     */
    maxStatefulOrdersPerNBlocks: MaxPerNBlocksRateLimit[];
    /** @deprecated */
    maxShortTermOrderCancellationsPerNBlocks: MaxPerNBlocksRateLimit[];
    maxShortTermOrdersAndCancelsPerNBlocks: MaxPerNBlocksRateLimit[];
}
/** Defines the block rate limits for CLOB specific operations. */
export interface BlockRateLimitConfigurationSDKType {
    /** @deprecated */
    max_short_term_orders_per_n_blocks: MaxPerNBlocksRateLimitSDKType[];
    max_stateful_orders_per_n_blocks: MaxPerNBlocksRateLimitSDKType[];
    /** @deprecated */
    max_short_term_order_cancellations_per_n_blocks: MaxPerNBlocksRateLimitSDKType[];
    max_short_term_orders_and_cancels_per_n_blocks: MaxPerNBlocksRateLimitSDKType[];
}
/** Defines a rate limit over a specific number of blocks. */
export interface MaxPerNBlocksRateLimit {
    /**
     * How many blocks the rate limit is over.
     * Specifying 0 is invalid.
     */
    numBlocks: number;
    /**
     * What the limit is for `num_blocks`.
     * Specifying 0 is invalid.
     */
    limit: number;
}
/** Defines a rate limit over a specific number of blocks. */
export interface MaxPerNBlocksRateLimitSDKType {
    num_blocks: number;
    limit: number;
}
export declare const BlockRateLimitConfiguration: {
    encode(message: BlockRateLimitConfiguration, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): BlockRateLimitConfiguration;
    fromPartial(object: DeepPartial<BlockRateLimitConfiguration>): BlockRateLimitConfiguration;
};
export declare const MaxPerNBlocksRateLimit: {
    encode(message: MaxPerNBlocksRateLimit, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): MaxPerNBlocksRateLimit;
    fromPartial(object: DeepPartial<MaxPerNBlocksRateLimit>): MaxPerNBlocksRateLimit;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 66
- Comment lines: 34
- Blank lines: -33

### Main Components



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

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/block_rate_limit_config.d.ts
```

