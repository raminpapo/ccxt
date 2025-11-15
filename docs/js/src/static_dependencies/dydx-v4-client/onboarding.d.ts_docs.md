# Documentation: js/src/static_dependencies/dydx-v4-client/onboarding.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/dydx-v4-client/onboarding.d.ts`
- **Size**: 1,046 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * @description Get Mnemonic and priv/pub keys from privateKeyBytes and BIP44 HD path
 *
 * @url https://github.com/confio/cosmos-hd-key-derivation-spec#bip44
 *
 * @param entropy used to generate mnemonic
 *
 * @param path BIP44 HD Path. Default is The Cosmos Hub path
 *
 * @throws Error if the hdkey does not exist
 *
 * @returns Mnemonic and priv/pub keys
 */
export declare const exportMnemonicAndPrivateKey: (entropy: Uint8Array, path?: string) => {
    mnemonic: string;
    privateKey: Uint8Array | null;
    publicKey: Uint8Array | null;
};
/**
 * @description Derive priv/pub keys from mnemonic and BIP44 HD path
 *
 * @url https://github.com/confio/cosmos-hd-key-derivation-spec#bip44
 *
 * @param mnemonic used to generate seed
 *
 * @param path BIP44 HD Path. Default is The Cosmos Hub path
 *
 * @throws Error if the hdkey does not exist
 *
 * @returns Priv/pub keys
 */
export declare const deriveHDKeyFromMnemonic: (mnemonic: string, path?: string) => {
    privateKey: Uint8Array | null;
    publicKey: Uint8Array | null;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/dydx-v4-client/onboarding.d.ts`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 35
- Comment lines: 26
- Blank lines: -25

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/dydx-v4-client/onboarding.d.ts
```

