# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/subaccount.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/subaccount.d.ts`
- **Size**: 2,265 bytes
- **Lines**: 63
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { AssetPosition, AssetPositionSDKType } from "./asset_position.js";
import { PerpetualPosition, PerpetualPositionSDKType } from "./perpetual_position.js";
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../helpers.js";
/** SubaccountId defines a unique identifier for a Subaccount. */
export interface SubaccountId {
    /** The address of the wallet that owns this subaccount. */
    owner: string;
    /**
     * The unique number of this subaccount for the owner.
     * Currently limited to 128*1000 subaccounts per owner.
     */
    number: number;
}
/** SubaccountId defines a unique identifier for a Subaccount. */
export interface SubaccountIdSDKType {
    owner: string;
    number: number;
}
/**
 * Subaccount defines a single sub-account for a given address.
 * Subaccounts are uniquely indexed by a subaccountNumber/owner pair.
 */
export interface Subaccount {
    /** The Id of the Subaccount */
    id?: SubaccountId;
    /**
     * All `AssetPosition`s associated with this subaccount.
     * Always sorted ascending by `asset_id`.
     */
    assetPositions: AssetPosition[];
    /**
     * All `PerpetualPosition`s associated with this subaccount.
     * Always sorted ascending by `perpetual_id.
     */
    perpetualPositions: PerpetualPosition[];
    /**
     * Set by the owner. If true, then margin trades can be made in this
     * subaccount.
     */
    marginEnabled: boolean;
}
/**
 * Subaccount defines a single sub-account for a given address.
 * Subaccounts are uniquely indexed by a subaccountNumber/owner pair.
 */
export interface SubaccountSDKType {
    id?: SubaccountIdSDKType;
    asset_positions: AssetPositionSDKType[];
    perpetual_positions: PerpetualPositionSDKType[];
    margin_enabled: boolean;
}
export declare const SubaccountId: {
    encode(message: SubaccountId, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): SubaccountId;
    fromPartial(object: DeepPartial<SubaccountId>): SubaccountId;
};
export declare const Subaccount: {
    encode(message: Subaccount, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): Subaccount;
    fromPartial(object: DeepPartial<Subaccount>): Subaccount;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/subaccount.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 62
- Comment lines: 28
- Blank lines: -27

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `./asset_position.js` (imported)
- `./perpetual_position.js` (imported)
- `../../helpers.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `./asset_position.js` (referenced)
- `./perpetual_position.js` (referenced)
- `../../helpers.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/dydx-v4-client/dydxprotocol/subaccounts/subaccount.d.ts
```

