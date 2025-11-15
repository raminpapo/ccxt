# Documentation: js/src/static_dependencies/starknet/constants.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/constants.js`
- **Size**: 2,626 bytes
- **Lines**: 62
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// import { ETransactionVersion } from './types/api';
export { IS_BROWSER } from './utils/encode.js';
/**
 * Cairo Felt support storing max 31 character
 */
export const TEXT_TO_FELT_MAX_LEN = 31;
/**
 * Alternatively use directly from api specification
 * types.RPC.ETransactionVersion
 * For BN do BigInt(TRANSACTION_VERSION.*)
 */
// export { ETransactionVersion as TRANSACTION_VERSION };
export const ZERO = 0n;
export const MASK_250 = 2n ** 250n - 1n; // 2 ** 250 - 1
export const API_VERSION = ZERO;
export const PRIME = 2n ** 251n + 17n * 2n ** 192n + 1n;
// based on: https://github.com/starkware-libs/cairo-lang/blob/v0.12.3/src/starkware/starknet/common/storage.cairo#L3
export const MAX_STORAGE_ITEM_SIZE = 256n;
export const ADDR_BOUND = 2n ** 251n - MAX_STORAGE_ITEM_SIZE;
const range = (min, max) => ({ min, max });
export const RANGE_FELT = range(ZERO, PRIME - 1n);
export const RANGE_I128 = range(-(2n ** 127n), 2n ** 127n - 1n);
export const RANGE_U128 = range(ZERO, 2n ** 128n - 1n);
export var BaseUrl;
(function (BaseUrl) {
    BaseUrl["SN_MAIN"] = "https://alpha-mainnet.starknet.io";
    BaseUrl["SN_SEPOLIA"] = "https://alpha-sepolia.starknet.io";
})(BaseUrl || (BaseUrl = {}));
export var NetworkName;
(function (NetworkName) {
    NetworkName["SN_MAIN"] = "SN_MAIN";
    NetworkName["SN_SEPOLIA"] = "SN_SEPOLIA";
})(NetworkName || (NetworkName = {}));
export var StarknetChainId;
(function (StarknetChainId) {
    StarknetChainId["SN_MAIN"] = "0x534e5f4d41494e";
    StarknetChainId["SN_SEPOLIA"] = "0x534e5f5345504f4c4941";
})(StarknetChainId || (StarknetChainId = {}));
export var TransactionHashPrefix;
(function (TransactionHashPrefix) {
    TransactionHashPrefix["DECLARE"] = "0x6465636c617265";
    TransactionHashPrefix["DEPLOY"] = "0x6465706c6f79";
    TransactionHashPrefix["DEPLOY_ACCOUNT"] = "0x6465706c6f795f6163636f756e74";
    TransactionHashPrefix["INVOKE"] = "0x696e766f6b65";
    TransactionHashPrefix["L1_HANDLER"] = "0x6c315f68616e646c6572";
})(TransactionHashPrefix || (TransactionHashPrefix = {}));
export const UDC = {
    ADDRESS: '0x041a78e741e5af2fec34b695679bc6891742439f7afb8484ecd7766661ad02bf',
    ENTRYPOINT: 'deployContract',
};
export const RPC_DEFAULT_VERSION = 'v0_7';
export const RPC_NODES = {
    SN_MAIN: [
        `https://starknet-mainnet.public.blastapi.io/rpc/${RPC_DEFAULT_VERSION}`,
        `https://free-rpc.nethermind.io/mainnet-juno/${RPC_DEFAULT_VERSION}`,
    ],
    SN_SEPOLIA: [
        `https://starknet-sepolia.public.blastapi.io/rpc/${RPC_DEFAULT_VERSION}`,
        `https://free-rpc.nethermind.io/sepolia-juno/${RPC_DEFAULT_VERSION}`,
    ],
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/constants.js`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 58
- Comment lines: 11
- Blank lines: -7

### Main Components

**Constants** (13):
- `ADDR_BOUND`
- `API_VERSION`
- `MASK_250`
- `MAX_STORAGE_ITEM_SIZE`
- `PRIME`
- `RANGE_FELT`
- `RANGE_I128`
- `RANGE_U128`
- `RPC_DEFAULT_VERSION`
- `RPC_NODES`
- `TEXT_TO_FELT_MAX_LEN`
- `UDC`
- `ZERO`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./types/api` (imported)
- `./utils/encode.js` (imported)
- `https://alpha-sepolia.starknet.io` (referenced)
- `https://alpha-mainnet.starknet.io` (referenced)
- `./utils/encode.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/constants.js
```

