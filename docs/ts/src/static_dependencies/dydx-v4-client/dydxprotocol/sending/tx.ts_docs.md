# Documentation: ts/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.ts`
- **Size**: 6,977 bytes
- **Lines**: 237
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

export interface MsgCreateTransferResponse {}
/** MsgCreateTransferResponse is a response type used for new transfers. */

export interface MsgCreateTransferResponseSDKType {}
/**
 * MsgDepositToSubaccountResponse is a response type used for new
 * account-to-subaccount transfers.
 */

export interface MsgDepositToSubaccountResponse {}
/**
 * MsgDepositToSubaccountResponse is a response type used for new
 * account-to-subaccount transfers.
 */

export interface MsgDepositToSubaccountResponseSDKType {}
/**
 * MsgWithdrawFromSubaccountResponse is a response type used for new
 * subaccount-to-account transfers.
 */

export interface MsgWithdrawFromSubaccountResponse {}
/**
 * MsgWithdrawFromSubaccountResponse is a response type used for new
 * subaccount-to-account transfers.
 */

export interface MsgWithdrawFromSubaccountResponseSDKType {}
/**
 * MsgSendFromModuleToAccountResponse is a response type used for new
 * module-to-account transfers.
 */

export interface MsgSendFromModuleToAccountResponse {}
/**
 * MsgSendFromModuleToAccountResponse is a response type used for new
 * module-to-account transfers.
 */

export interface MsgSendFromModuleToAccountResponseSDKType {}

function createBaseMsgCreateTransfer(): MsgCreateTransfer {
  return {
    transfer: undefined
  };
}

export const MsgCreateTransfer = {
  encode(message: MsgCreateTransfer, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    if (message.transfer !== undefined) {
      Transfer.encode(message.transfer, writer.uint32(10).fork()).ldelim();
    }

    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): MsgCreateTransfer {
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

  fromPartial(object: DeepPartial<MsgCreateTransfer>): MsgCreateTransfer {
    const message = createBaseMsgCreateTransfer();
    message.transfer = object.transfer !== undefined && object.transfer !== null ? Transfer.fromPartial(object.transfer) : undefined;
    return message;
  }

};

function createBaseMsgCreateTransferResponse(): MsgCreateTransferResponse {
  return {};
}

export const MsgCreateTransferResponse = {
  encode(_: MsgCreateTransferResponse, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): MsgCreateTransferResponse {
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

  fromPartial(_: DeepPartial<MsgCreateTransferResponse>): MsgCreateTransferResponse {
    const message = createBaseMsgCreateTransferResponse();
    return message;
  }

};

function createBaseMsgDepositToSubaccountResponse(): MsgDepositToSubaccountResponse {
  return {};
}

export const MsgDepositToSubaccountResponse = {
  encode(_: MsgDepositToSubaccountResponse, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): MsgDepositToSubaccountResponse {
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

  fromPartial(_: DeepPartial<MsgDepositToSubaccountResponse>): MsgDepositToSubaccountResponse {
    const message = createBaseMsgDepositToSubaccountResponse();
    return message;
  }

};

function createBaseMsgWithdrawFromSubaccountResponse(): MsgWithdrawFromSubaccountResponse {
  return {};
}

export const MsgWithdrawFromSubaccountResponse = {
  encode(_: MsgWithdrawFromSubaccountResponse, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): MsgWithdrawFromSubaccountResponse {
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

  fromPartial(_: DeepPartial<MsgWithdrawFromSubaccountResponse>): MsgWithdrawFromSubaccountResponse {
    const message = createBaseMsgWithdrawFromSubaccountResponse();
    return message;
  }

};

function createBaseMsgSendFromModuleToAccountResponse(): MsgSendFromModuleToAccountResponse {
  return {};
}

export const MsgSendFromModuleToAccountResponse = {
  encode(_: MsgSendFromModuleToAccountResponse, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): MsgSendFromModuleToAccountResponse {
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

  fromPartial(_: DeepPartial<MsgSendFromModuleToAccountResponse>): MsgSendFromModuleToAccountResponse {
    const message = createBaseMsgSendFromModuleToAccountResponse();
    return message;
  }

};
```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.ts`.

**Functions defined**: createBaseMsgCreateTransfer, createBaseMsgWithdrawFromSubaccountResponse, createBaseMsgCreateTransferResponse, createBaseMsgDepositToSubaccountResponse, createBaseMsgSendFromModuleToAccountResponse

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 237
- Code lines: 185
- Comment lines: 29
- Blank lines: 23

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
- `../../helpers.js` (imported)
- `./transfer.js` (referenced)
- `protobufjs/minimal.js` (referenced)
- `../../helpers.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/dydx-v4-client/dydxprotocol/sending/tx.ts
```

