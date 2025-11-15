# Documentation: ts/src/static_dependencies/ethers/address/contract-address.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/address/contract-address.ts`
- **Size**: 2,659 bytes
- **Lines**: 81
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import {
    concat, dataSlice, getBigInt, getBytes, encodeRlp, assertArgument,
    keccak256
} from "../utils/index.js";

import { getAddress } from "./address.js";

import type { BigNumberish, BytesLike } from "../utils/index.js";


// http://ethereum.stackexchange.com/questions/760/how-is-the-address-of-an-ethereum-contract-computed

/**
 *  Returns the address that would result from a ``CREATE`` for %%tx%%.
 *
 *  This can be used to compute the address a contract will be
 *  deployed to by an EOA when sending a deployment transaction (i.e.
 *  when the ``to`` address is ``null``).
 *
 *  This can also be used to compute the address a contract will be
 *  deployed to by a contract, by using the contract's address as the
 *  ``to`` and the contract's nonce.
 *
 *  @example
 *    from = "0x8ba1f109551bD432803012645Ac136ddd64DBA72";
 *    nonce = 5;
 *
 *    getCreateAddress({ from, nonce });
 *    //_result:
 */
export function getCreateAddress(tx: { from: string, nonce: BigNumberish }): string {
    const from = getAddress(tx.from);
    const nonce = getBigInt(tx.nonce, "tx.nonce");

    let nonceHex = nonce.toString(16);
    if (nonceHex === "0") {
        nonceHex = "0x";
    } else if (nonceHex.length % 2) {
        nonceHex = "0x0" + nonceHex;
    } else {
        nonceHex = "0x" + nonceHex;
    }

    return getAddress(dataSlice(keccak256(encodeRlp([ from, nonceHex ])), 12));
}

/**
 *  Returns the address that would result from a ``CREATE2`` operation
 *  with the given %%from%%, %%salt%% and %%initCodeHash%%.
 *
 *  To compute the %%initCodeHash%% from a contract's init code, use
 *  the [[keccak256]] function.
 *
 *  For a quick overview and example of ``CREATE2``, see [[link-ricmoo-wisps]].
 *
 *  @example
 *    // The address of the contract
 *    from = "0x8ba1f109551bD432803012645Ac136ddd64DBA72"
 *
 *    // The salt
 *    salt = id("HelloWorld")
 *
 *    // The hash of the initCode
 *    initCode = "0x6394198df16000526103ff60206004601c335afa6040516060f3";
 *    initCodeHash = keccak256(initCode)
 *
 *    getCreate2Address(from, salt, initCodeHash)
 *    //_result:
 */
export function getCreate2Address(_from: string, _salt: BytesLike, _initCodeHash: BytesLike): string {
    const from = getAddress(_from);
    const salt = getBytes(_salt, "salt");
    const initCodeHash = getBytes(_initCodeHash, "initCodeHash");

    assertArgument(salt.length === 32, "salt must be 32 bytes", "salt", _salt);

    assertArgument(initCodeHash.length === 32, "initCodeHash must be 32 bytes", "initCodeHash", _initCodeHash);

    return getAddress(dataSlice(keccak256(concat([ "0xff", from, salt, initCodeHash ])), 12))
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/address/contract-address.ts`.

**Functions defined**: getCreateAddress, getCreate2Address

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 68
- Comment lines: 42
- Blank lines: -29

### Main Components

**Functions** (2):
- `getCreate2Address()`
- `getCreateAddress()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./address.js` (imported)
- `../utils/index.js` (imported)
- `./address.js` (referenced)
- `../utils/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/address/contract-address.ts
```

