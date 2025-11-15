# Documentation: js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/finalize_block.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/finalize_block.d.ts`
- **Size**: 906 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { ClobPair, ClobPairSDKType } from "./clob_pair.js";
import _m0 from "protobufjs/minimal.js";
import { DeepPartial } from "../../helpers.js";
/**
 * ClobStagedFinalizeBlockEvent defines a CLOB event staged during
 * FinalizeBlock.
 */
export interface ClobStagedFinalizeBlockEvent {
    /** create_clob_pair indicates a new CLOB pair creation. */
    createClobPair?: ClobPair;
}
/**
 * ClobStagedFinalizeBlockEvent defines a CLOB event staged during
 * FinalizeBlock.
 */
export interface ClobStagedFinalizeBlockEventSDKType {
    create_clob_pair?: ClobPairSDKType;
}
export declare const ClobStagedFinalizeBlockEvent: {
    encode(message: ClobStagedFinalizeBlockEvent, writer?: _m0.Writer): _m0.Writer;
    decode(input: _m0.Reader | Uint8Array, length?: number): ClobStagedFinalizeBlockEvent;
    fromPartial(object: DeepPartial<ClobStagedFinalizeBlockEvent>): ClobStagedFinalizeBlockEvent;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/finalize_block.d.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 23
- Comment lines: 9
- Blank lines: -8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `protobufjs/minimal.js` (imported)
- `./clob_pair.js` (imported)
- `../../helpers.js` (imported)
- `protobufjs/minimal.js` (referenced)
- `./clob_pair.js` (referenced)
- `../../helpers.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/dydx-v4-client/dydxprotocol/clob/finalize_block.d.ts
```

