# Documentation: ts/src/static_dependencies/dydx-v4-client/onboarding.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/dydx-v4-client/onboarding.ts`
- **Size**: 1,777 bytes
- **Lines**: 69
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { HDKey } from '../scure-bip32/index.js';
import { entropyToMnemonic, mnemonicToSeedSync } from '../scure-bip39/index.js';
import { wordlist } from '../scure-bip39/wordlists/english.js';

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
export const exportMnemonicAndPrivateKey = (
  entropy: Uint8Array,
  path: string = "m/44'/118'/0'/0/0",
): {
  mnemonic: string;
  privateKey: Uint8Array | null;
  publicKey: Uint8Array | null;
} => {
  const mnemonic = entropyToMnemonic(entropy, wordlist);
  const { privateKey, publicKey } = deriveHDKeyFromMnemonic(mnemonic, path);
  return {
    mnemonic,
    privateKey,
    publicKey,
  };
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
export const deriveHDKeyFromMnemonic = (
  mnemonic: string,
  path: string = "m/44'/118'/0'/0/0",
): {
  privateKey: Uint8Array | null;
  publicKey: Uint8Array | null;
} => {
  const seed = mnemonicToSeedSync(mnemonic);

  const hdkey = HDKey.fromMasterSeed(seed);
  const derivedHdkey = hdkey.derive(path);

  if (!hdkey.privateKey) {
    throw new Error('null hd key');
  }

  return {
    privateKey: derivedHdkey.privateKey,
    publicKey: derivedHdkey.publicKey,
  };
};

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/dydx-v4-client/onboarding.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 69
- Code lines: 63
- Comment lines: 26
- Blank lines: -20

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../scure-bip32/index.js` (imported)
- `../scure-bip39/wordlists/english.js` (imported)
- `../scure-bip39/index.js` (imported)
- `../scure-bip32/index.js` (referenced)
- `../scure-bip39/wordlists/english.js` (referenced)
- `../scure-bip39/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/dydx-v4-client/onboarding.ts
```

