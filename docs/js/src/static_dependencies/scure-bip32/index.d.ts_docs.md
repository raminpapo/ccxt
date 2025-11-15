# Documentation: js/src/static_dependencies/scure-bip32/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/scure-bip32/index.d.ts`
- **Size**: 1,455 bytes
- **Lines**: 50
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare const HARDENED_OFFSET: number;
export interface Versions {
    private: number;
    public: number;
}
interface HDKeyOpt {
    versions?: Versions;
    depth?: number;
    index?: number;
    parentFingerprint?: number;
    chainCode?: Uint8Array;
    publicKey?: Uint8Array;
    privateKey?: Uint8Array | bigint;
}
export declare class HDKey {
    get fingerprint(): number;
    get identifier(): Uint8Array | undefined;
    get pubKeyHash(): Uint8Array | undefined;
    get privateKey(): Uint8Array | null;
    get publicKey(): Uint8Array | null;
    get privateExtendedKey(): string;
    get publicExtendedKey(): string;
    static fromMasterSeed(seed: Uint8Array, versions?: Versions): HDKey;
    static fromExtendedKey(base58key: string, versions?: Versions): HDKey;
    static fromJSON(json: {
        xpriv: string;
    }): HDKey;
    readonly versions: Versions;
    readonly depth: number;
    readonly index: number;
    readonly chainCode: Uint8Array | null;
    readonly parentFingerprint: number;
    private privKey?;
    private privKeyBytes?;
    private pubKey?;
    private pubHash;
    constructor(opt: HDKeyOpt);
    derive(path: string): HDKey;
    deriveChild(index: number): HDKey;
    sign(hash: Uint8Array): Uint8Array;
    verify(hash: Uint8Array, signature: Uint8Array): boolean;
    wipePrivateData(): this;
    toJSON(): {
        xpriv: string;
        xpub: string;
    };
    private serialize;
}
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/scure-bip32/index.d.ts`.

**Classes defined**: HDKey



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 49
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `HDKey`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/scure-bip32/index.d.ts
```

