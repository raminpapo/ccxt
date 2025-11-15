# Documentation: js/src/static_dependencies/dydx-v4-client/registry.js

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/registry.js`
- **Size**: 1,358 bytes
- **Lines**: 31
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { PubKey } from './cosmos/crypto/secp256k1/keys.js';
import { TxExtension } from './dydxprotocol/accountplus/tx.js';
import { MsgPlaceOrder, MsgCancelOrder, MsgBatchCancel, } from './dydxprotocol/clob/tx.js';
import { MsgWithdrawFromSubaccount, MsgDepositToSubaccount, } from './dydxprotocol/sending/transfer.js';
import { MsgCreateTransfer } from './dydxprotocol/sending/tx.js';
import { Any } from "./google/protobuf/any.js";
export const registry = {
    // clob
    '/dydxprotocol.clob.MsgPlaceOrder': MsgPlaceOrder,
    '/dydxprotocol.clob.MsgCancelOrder': MsgCancelOrder,
    '/dydxprotocol.clob.MsgBatchCancel': MsgBatchCancel,
    // sending
    '/dydxprotocol.sending.MsgCreateTransfer': MsgCreateTransfer,
    '/dydxprotocol.sending.MsgWithdrawFromSubaccount': MsgWithdrawFromSubaccount,
    '/dydxprotocol.sending.MsgDepositToSubaccount': MsgDepositToSubaccount,
    '/dydxprotocol.accountplus.TxExtension': TxExtension,
    '/cosmos.crypto.secp256k1.PubKey': PubKey,
};
export function encodeAsAny(encodeObject) {
    const { typeUrl, value } = encodeObject;
    const type = registry[typeUrl];
    if (!type) {
        throw new Error(`Unsupport type url: ${typeUrl}`);
    }
    const encodedMsg = type.encode(type.fromPartial(value)).finish();
    return Any.fromPartial({
        typeUrl: typeUrl,
        value: encodedMsg,
    });
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/dydx-v4-client/registry.js`.

**Functions defined**: encodeAsAny

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 28
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `encodeAsAny()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./dydxprotocol/clob/tx.js` (imported)
- `./google/protobuf/any.js` (imported)
- `./cosmos/crypto/secp256k1/keys.js` (imported)
- `./dydxprotocol/sending/tx.js` (imported)
- `./dydxprotocol/accountplus/tx.js` (imported)
- `./dydxprotocol/sending/transfer.js` (imported)
- `./dydxprotocol/clob/tx.js` (referenced)
- `./google/protobuf/any.js` (referenced)
- `./cosmos/crypto/secp256k1/keys.js` (referenced)
- `./dydxprotocol/sending/tx.js` (referenced)
- `./dydxprotocol/accountplus/tx.js` (referenced)
- `./dydxprotocol/sending/transfer.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/dydx-v4-client/registry.js
```

