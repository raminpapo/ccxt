# Documentation: js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.d.ts`
- **Size**: 916 bytes
- **Lines**: 27
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Any, AnySDKType } from "../../../google/protobuf/any.js";
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../../helpers.js";
/**
 * LegacyAminoPubKey specifies a public key type
 * which nests multiple public keys and a threshold,
 * it uses legacy amino address rules.
 */
export interface LegacyAminoPubKey {
    threshold: number;
    publicKeys: Any[];
}
/**
 * LegacyAminoPubKey specifies a public key type
 * which nests multiple public keys and a threshold,
 * it uses legacy amino address rules.
 */
export interface LegacyAminoPubKeySDKType {
    threshold: number;
    public_keys: AnySDKType[];
}
export declare const LegacyAminoPubKey: {
    encode(message: LegacyAminoPubKey, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): LegacyAminoPubKey;
    fromPartial(object: DeepPartial<LegacyAminoPubKey>): LegacyAminoPubKey;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
- Comment lines: 10
- Blank lines: -9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `../../../helpers.js` (imported)
- `../../../google/protobuf/any.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `../../../helpers.js` (referenced)
- `../../../google/protobuf/any.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/dydx-v4-client/cosmos/crypto/multisig/keys.d.ts
```

