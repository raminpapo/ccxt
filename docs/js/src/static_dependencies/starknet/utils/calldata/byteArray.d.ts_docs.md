# Documentation: js/src/static_dependencies/starknet/utils/calldata/byteArray.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/byteArray.d.ts`
- **Size**: 920 bytes
- **Lines**: 33
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { ByteArray } from '../../types/lib/index.js';
/**
 * convert a Cairo ByteArray to a JS string
 * @param myByteArray Cairo representation of a LongString
 * @returns a JS string
 * @example
 * ```typescript
 * const myByteArray = {
 *    data: [],
 *    pending_word: '0x414243444546474849',
 *    pending_word_len: 9
 * }
 * const result: String = stringFromByteArray(myByteArray); // ABCDEFGHI
 * ```
 */
export declare function stringFromByteArray(myByteArray: ByteArray): string;
/**
 * convert a JS string to a Cairo ByteArray
 * @param targetString a JS string
 * @returns Cairo representation of a LongString
 * @example
 * ```typescript
 * const myByteArray: ByteArray = byteArrayFromString("ABCDEFGHI");
 * ```
 * Result is :
 * {
 *    data: [],
 *    pending_word: '0x414243444546474849',
 *    pending_word_len: 9
 * }
 */
export declare function byteArrayFromString(targetString: string): ByteArray;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/byteArray.d.ts`.

**Functions defined**: stringFromByteArray, byteArrayFromString

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 32
- Comment lines: 29
- Blank lines: -28

### Main Components

**Functions** (2):
- `byteArrayFromString()`
- `stringFromByteArray()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../types/lib/index.js` (imported)
- `../../types/lib/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/calldata/byteArray.d.ts
```

