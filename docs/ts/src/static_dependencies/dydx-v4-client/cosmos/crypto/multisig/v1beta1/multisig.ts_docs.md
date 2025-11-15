# Documentation: ts/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.ts`
- **Size**: 3,783 bytes
- **Lines**: 142
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../../../helpers.js";
/**
 * MultiSignature wraps the signatures from a multisig.LegacyAminoPubKey.
 * See cosmos.tx.v1betata1.ModeInfo.Multi for how to specify which signers
 * signed and with which modes.
 */

export interface MultiSignature {
  signatures: Uint8Array[];
}
/**
 * MultiSignature wraps the signatures from a multisig.LegacyAminoPubKey.
 * See cosmos.tx.v1betata1.ModeInfo.Multi for how to specify which signers
 * signed and with which modes.
 */

export interface MultiSignatureSDKType {
  signatures: Uint8Array[];
}
/**
 * CompactBitArray is an implementation of a space efficient bit array.
 * This is used to ensure that the encoded data takes up a minimal amount of
 * space after proto encoding.
 * This is not thread safe, and is not intended for concurrent usage.
 */

export interface CompactBitArray {
  extraBitsStored: number;
  elems: Uint8Array;
}
/**
 * CompactBitArray is an implementation of a space efficient bit array.
 * This is used to ensure that the encoded data takes up a minimal amount of
 * space after proto encoding.
 * This is not thread safe, and is not intended for concurrent usage.
 */

export interface CompactBitArraySDKType {
  extra_bits_stored: number;
  elems: Uint8Array;
}

function createBaseMultiSignature(): MultiSignature {
  return {
    signatures: []
  };
}

export const MultiSignature = {
  encode(message: MultiSignature, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    for (const v of message.signatures) {
      writer.uint32(10).bytes(v!);
    }

    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): MultiSignature {
    const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
    let end = length === undefined ? reader.len : reader.pos + length;
    const message = createBaseMultiSignature();

    while (reader.pos < end) {
      const tag = reader.uint32();

      switch (tag >>> 3) {
        case 1:
          message.signatures.push(reader.bytes());
          break;

        default:
          reader.skipType(tag & 7);
          break;
      }
    }

    return message;
  },

  fromPartial(object: DeepPartial<MultiSignature>): MultiSignature {
    const message = createBaseMultiSignature();
    message.signatures = object.signatures?.map(e => e) || [];
    return message;
  }

};

function createBaseCompactBitArray(): CompactBitArray {
  return {
    extraBitsStored: 0,
    elems: new Uint8Array()
  };
}

export const CompactBitArray = {
  encode(message: CompactBitArray, writer: _m0.Writer = _m0.Writer.create()): _m0.Writer {
    if (message.extraBitsStored !== 0) {
      writer.uint32(8).uint32(message.extraBitsStored);
    }

    if (message.elems.length !== 0) {
      writer.uint32(18).bytes(message.elems);
    }

    return writer;
  },

  decode(input: _m0.Reader | Uint8Array, length?: number): CompactBitArray {
    const reader = input instanceof _m0.Reader ? input : new _m0.Reader(input);
    let end = length === undefined ? reader.len : reader.pos + length;
    const message = createBaseCompactBitArray();

    while (reader.pos < end) {
      const tag = reader.uint32();

      switch (tag >>> 3) {
        case 1:
          message.extraBitsStored = reader.uint32();
          break;

        case 2:
          message.elems = reader.bytes();
          break;

        default:
          reader.skipType(tag & 7);
          break;
      }
    }

    return message;
  },

  fromPartial(object: DeepPartial<CompactBitArray>): CompactBitArray {
    const message = createBaseCompactBitArray();
    message.extraBitsStored = object.extraBitsStored ?? 0;
    message.elems = object.elems ?? new Uint8Array();
    return message;
  }

};
```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.ts`.

**Functions defined**: createBaseCompactBitArray, createBaseMultiSignature

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 142
- Code lines: 116
- Comment lines: 22
- Blank lines: 4

### Main Components

**Functions** (2):
- `createBaseCompactBitArray()`
- `createBaseMultiSignature()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `../../../../helpers.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `../../../../helpers.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/v1beta1/multisig.ts
```

