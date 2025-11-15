# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.d.ts`
- **Size**: 3,390 bytes
- **Lines**: 80
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Transfer, TransferSDKType } from "./transfer.js";
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../helpers.js";
/** MsgCreateTransfer is a request type used for initiating new transfers. */
export interface MsgCreateTransfer {
    /** MsgCreateTransfer is a request type used for initiating new transfers. */
    transfer?: Transfer;
}
/** MsgCreateTransfer is a request type used for initiating new transfers. */
export interface MsgCreateTransferSDKType {
    transfer?: TransferSDKType;
}
/** MsgCreateTransferResponse is a response type used for new transfers. */
export interface MsgCreateTransferResponse {
}
/** MsgCreateTransferResponse is a response type used for new transfers. */
export interface MsgCreateTransferResponseSDKType {
}
/**
 * MsgDepositToSubaccountResponse is a response type used for new
 * account-to-subaccount transfers.
 */
export interface MsgDepositToSubaccountResponse {
}
/**
 * MsgDepositToSubaccountResponse is a response type used for new
 * account-to-subaccount transfers.
 */
export interface MsgDepositToSubaccountResponseSDKType {
}
/**
 * MsgWithdrawFromSubaccountResponse is a response type used for new
 * subaccount-to-account transfers.
 */
export interface MsgWithdrawFromSubaccountResponse {
}
/**
 * MsgWithdrawFromSubaccountResponse is a response type used for new
 * subaccount-to-account transfers.
 */
export interface MsgWithdrawFromSubaccountResponseSDKType {
}
/**
 * MsgSendFromModuleToAccountResponse is a response type used for new
 * module-to-account transfers.
 */
export interface MsgSendFromModuleToAccountResponse {
}
/**
 * MsgSendFromModuleToAccountResponse is a response type used for new
 * module-to-account transfers.
 */
export interface MsgSendFromModuleToAccountResponseSDKType {
}
export declare const MsgCreateTransfer: {
    encode(message: MsgCreateTransfer, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): MsgCreateTransfer;
    fromPartial(object: DeepPartial<MsgCreateTransfer>): MsgCreateTransfer;
};
export declare const MsgCreateTransferResponse: {
    encode(_: MsgCreateTransferResponse, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): MsgCreateTransferResponse;
    fromPartial(_: DeepPartial<MsgCreateTransferResponse>): MsgCreateTransferResponse;
};
export declare const MsgDepositToSubaccountResponse: {
    encode(_: MsgDepositToSubaccountResponse, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): MsgDepositToSubaccountResponse;
    fromPartial(_: DeepPartial<MsgDepositToSubaccountResponse>): MsgDepositToSubaccountResponse;
};
export declare const MsgWithdrawFromSubaccountResponse: {
    encode(_: MsgWithdrawFromSubaccountResponse, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): MsgWithdrawFromSubaccountResponse;
    fromPartial(_: DeepPartial<MsgWithdrawFromSubaccountResponse>): MsgWithdrawFromSubaccountResponse;
};
export declare const MsgSendFromModuleToAccountResponse: {
    encode(_: MsgSendFromModuleToAccountResponse, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): MsgSendFromModuleToAccountResponse;
    fromPartial(_: DeepPartial<MsgSendFromModuleToAccountResponse>): MsgSendFromModuleToAccountResponse;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 79
- Comment lines: 29
- Blank lines: -28

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./transfer.js` (imported)
- `protobufjs/minimal.js` (imported)
- `../../helpers.js` (imported)
- `./transfer.js` (referenced)
- `protobufjs/minimal.js` (referenced)
- `../../helpers.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.d.ts
```

