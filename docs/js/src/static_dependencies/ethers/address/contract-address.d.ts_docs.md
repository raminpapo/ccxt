# Documentation: js/src/static_dependencies/ethers/address/contract-address.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/address/contract-address.d.ts`
- **Size**: 1,578 bytes
- **Lines**: 48
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import type { BigNumberish, BytesLike } from "../utils/index.js";
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
export declare function getCreateAddress(tx: {
    from: string;
    nonce: BigNumberish;
}): string;
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
export declare function getCreate2Address(_from: string, _salt: BytesLike, _initCodeHash: BytesLike): string;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/address/contract-address.d.ts`.

**Functions defined**: getCreateAddress, getCreate2Address

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 47
- Comment lines: 41
- Blank lines: -40

### Main Components

**Functions** (2):
- `getCreate2Address()`
- `getCreateAddress()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../utils/index.js` (imported)
- `../utils/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/address/contract-address.d.ts
```

