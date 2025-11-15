# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.d.ts`
- **Size**: 1,217 bytes
- **Lines**: 35
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import * as _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../helpers.js";
/**
 * PerpetualPositions are an account’s positions of a `Perpetual`.
 * Therefore they hold any information needed to trade perpetuals.
 */
export interface PerpetualPosition {
    /** The `Id` of the `Perpetual`. */
    perpetualId: number;
    /** The size of the position in base quantums. */
    quantums: Uint8Array;
    /**
     * The funding_index of the `Perpetual` the last time this position was
     * settled.
     */
    fundingIndex: Uint8Array;
    /** The quote_balance of the `Perpetual`. */
    quoteBalance: Uint8Array;
}
/**
 * PerpetualPositions are an account’s positions of a `Perpetual`.
 * Therefore they hold any information needed to trade perpetuals.
 */
export interface PerpetualPositionSDKType {
    perpetual_id: number;
    quantums: Uint8Array;
    funding_index: Uint8Array;
    quote_balance: Uint8Array;
}
export declare const PerpetualPosition: {
    encode(message: PerpetualPosition, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): PerpetualPosition;
    fromPartial(object: DeepPartial<PerpetualPosition>): PerpetualPosition;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 34
- Comment lines: 15
- Blank lines: -14

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
ts-node js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/perpetual_position.d.ts
```

