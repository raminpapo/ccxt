# Documentation: ts/src/static_dependencies/ethers/address/checks.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/address/checks.ts`
- **Size**: 3,850 bytes
- **Lines**: 124
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { assert, assertArgument } from "../utils/index.js";

import { getAddress } from "./address.js";

import type { Addressable, AddressLike, NameResolver } from "./index.js";


/**
 *  Returns true if %%value%% is an object which implements the
 *  [[Addressable]] interface.
 *
 *  @example:
 *    // Wallets and AbstractSigner sub-classes
 *    isAddressable(Wallet.createRandom())
 *    //_result:
 *
 *    // Contracts
 *    contract = new Contract("dai.tokens.ethers.eth", [ ], provider)
 *    isAddressable(contract)
 *    //_result:
 */
export function isAddressable(value: any): value is Addressable {
    return (value && typeof(value.getAddress) === "function");
}

/**
 *  Returns true if %%value%% is a valid address.
 *
 *  @example:
 *    // Valid address
 *    isAddress("0x8ba1f109551bD432803012645Ac136ddd64DBA72")
 *    //_result:
 *
 *    // Valid ICAP address
 *    isAddress("XE65GB6LDNXYOFTX0NSV3FUWKOWIXAMJK36")
 *    //_result:
 *
 *    // Invalid checksum
 *    isAddress("0x8Ba1f109551bD432803012645Ac136ddd64DBa72")
 *    //_result:
 *
 *    // Invalid ICAP checksum
 *    isAddress("0x8Ba1f109551bD432803012645Ac136ddd64DBA72")
 *    //_result:
 *
 *    // Not an address (an ENS name requires a provided and an
 *    // asynchronous API to access)
 *    isAddress("ricmoo.eth")
 *    //_result:
 */
export function isAddress(value: any): value is string {
    try {
        getAddress(value);
        return true;
    } catch (error) { }
    return false;
}

async function checkAddress(target: any, promise: Promise<null | string>): Promise<string> {
    const result = await promise;
    if (result == null || result === "0x0000000000000000000000000000000000000000") {
        assert(typeof(target) !== "string", "unconfigured name", "UNCONFIGURED_NAME", { value: target });
        assertArgument(false, "invalid AddressLike value; did not resolve to a value address", "target", target);
    }
    return getAddress(result);
}

/**
 *  Resolves to an address for the %%target%%, which may be any
 *  supported address type, an [[Addressable]] or a Promise which
 *  resolves to an address.
 *
 *  If an ENS name is provided, but that name has not been correctly
 *  configured a [[UnconfiguredNameError]] is thrown.
 *
 *  @example:
 *    addr = "0x6B175474E89094C44Da98b954EedeAC495271d0F"
 *
 *    // Addresses are return synchronously
 *    resolveAddress(addr, provider)
 *    //_result:
 *
 *    // Address promises are resolved asynchronously
 *    resolveAddress(Promise.resolve(addr))
 *    //_result:
 *
 *    // ENS names are resolved asynchronously
 *    resolveAddress("dai.tokens.ethers.eth", provider)
 *    //_result:
 *
 *    // Addressable objects are resolved asynchronously
 *    contract = new Contract(addr, [ ])
 *    resolveAddress(contract, provider)
 *    //_result:
 *
 *    // Unconfigured ENS names reject
 *    resolveAddress("nothing-here.ricmoo.eth", provider)
 *    //_error:
 *
 *    // ENS names require a NameResolver object passed in
 *    // (notice the provider was omitted)
 *    resolveAddress("nothing-here.ricmoo.eth")
 *    //_error:
 */
export function resolveAddress(target: AddressLike, resolver?: null | NameResolver): string | Promise<string> {

    if (typeof(target) === "string") {
        if (target.match(/^0x[0-9a-f]{40}$/i)) { return getAddress(target); }

        assert(resolver != null, "ENS resolution requires a provider",
            "UNSUPPORTED_OPERATION", { operation: "resolveName" });

        return checkAddress(target, resolver.resolveName(target));

    } else if (isAddressable(target)) {
        return checkAddress(target, target.getAddress());

    } else if (target && typeof(target.then) === "function") {
        return checkAddress(target, target);
    }

    assertArgument(false, "unsupported addressable value", "target", target);
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/address/checks.ts`.

**Functions defined**: isAddress, isAddressable, resolveAddress, checkAddress

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 124
- Code lines: 110
- Comment lines: 76
- Blank lines: -62

### Main Components

**Functions** (4):
- `checkAddress()`
- `isAddress()`
- `isAddressable()`
- `resolveAddress()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./address.js` (imported)
- `../utils/index.js` (imported)
- `./index.js` (imported)
- `./address.js` (referenced)
- `../utils/index.js` (referenced)
- `./index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/address/checks.ts
```

