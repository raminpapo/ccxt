# Documentation: js/src/static_dependencies/noble-hashes/eskdf.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/eskdf.d.ts`
- **Size**: 1,653 bytes
- **Lines**: 47
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare function scrypt(password: string, salt: string): Uint8Array;
export declare function pbkdf2(password: string, salt: string): Uint8Array;
/**
 * Derives main seed. Takes a lot of time. Prefer `eskdf` method instead.
 */
export declare function deriveMainSeed(username: string, password: string): Uint8Array;
declare type AccountID = number | string;
declare type OptsLength = {
    keyLength: number;
};
declare type OptsMod = {
    modulus: bigint;
};
declare type KeyOpts = undefined | OptsLength | OptsMod;
declare type ESKDF = Promise<Readonly<{
    /**
     * Derives a child key. Child key will not be associated with any
     * other child key because of properties of underlying KDF.
     *
     * @param protocol - 3-15 character protocol name
     * @param accountId - numeric identifier of account
     * @param options - `keyLength: 64` or `modulus: 41920438n`
     * @example deriveChildKey('aes', 0)
     */
    deriveChildKey: (protocol: string, accountId: AccountID, options?: KeyOpts) => Uint8Array;
    /**
     * Deletes the main seed from eskdf instance
     */
    expire: () => void;
    /**
     * Account fingerprint
     */
    fingerprint: string;
}>>;
/**
 * ESKDF
 * @param username - username, email, or identifier, min: 8 characters, should have enough entropy
 * @param password - password, min: 8 characters, should have enough entropy
 * @example
 * const kdf = await eskdf('example-university', 'beginning-new-example');
 * const key = kdf.deriveChildKey('aes', 0);
 * console.log(kdf.fingerprint);
 * kdf.expire();
 */
export declare function eskdf(username: string, password: string): ESKDF;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/eskdf.d.ts`.

**Functions defined**: eskdf, pbkdf2, deriveMainSeed, scrypt

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 46
- Comment lines: 28
- Blank lines: -27

### Main Components

**Functions** (4):
- `deriveMainSeed()`
- `eskdf()`
- `pbkdf2()`
- `scrypt()`

**Constants** (1):
- `ESKDF`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/eskdf.d.ts
```

