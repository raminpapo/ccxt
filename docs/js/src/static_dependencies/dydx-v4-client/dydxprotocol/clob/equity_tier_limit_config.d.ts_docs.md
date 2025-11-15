# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.d.ts`
- **Size**: 1,883 bytes
- **Lines**: 49
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../helpers.js";
/**
 * Defines the set of equity tiers to limit how many open orders
 * a subaccount is allowed to have.
 */
export interface EquityTierLimitConfiguration {
    /**
     * How many short term stateful orders are allowed per equity tier.
     * Specifying 0 values disables this limit.
     */
    shortTermOrderEquityTiers: EquityTierLimit[];
    /**
     * How many open stateful orders are allowed per equity tier.
     * Specifying 0 values disables this limit.
     */
    statefulOrderEquityTiers: EquityTierLimit[];
}
/**
 * Defines the set of equity tiers to limit how many open orders
 * a subaccount is allowed to have.
 */
export interface EquityTierLimitConfigurationSDKType {
    short_term_order_equity_tiers: EquityTierLimitSDKType[];
    stateful_order_equity_tiers: EquityTierLimitSDKType[];
}
/** Defines an equity tier limit. */
export interface EquityTierLimit {
    /** The total net collateral in USDC quote quantums of equity required. */
    usdTncRequired: Uint8Array;
    /** What the limit is for `usd_tnc_required`. */
    limit: number;
}
/** Defines an equity tier limit. */
export interface EquityTierLimitSDKType {
    usd_tnc_required: Uint8Array;
    limit: number;
}
export declare const EquityTierLimitConfiguration: {
    encode(message: EquityTierLimitConfiguration, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): EquityTierLimitConfiguration;
    fromPartial(object: DeepPartial<EquityTierLimitConfiguration>): EquityTierLimitConfiguration;
};
export declare const EquityTierLimit: {
    encode(message: EquityTierLimit, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): EquityTierLimit;
    fromPartial(object: DeepPartial<EquityTierLimit>): EquityTierLimit;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 48
- Comment lines: 20
- Blank lines: -19

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
ts-node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/equity_tier_limit_config.d.ts
```

