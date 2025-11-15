# Documentation: ts/src/static_dependencies/starknet/utils/calldata/byteArray.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/byteArray.ts`
- **Size**: 2,020 bytes
- **Lines**: 64
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BigNumberish, ByteArray } from '../../types/lib/index.js';
import { toHex } from '../num.js';
import { decodeShortString, encodeShortString, splitLongString } from '../shortString.js';

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
export function stringFromByteArray(myByteArray: ByteArray): string {
  const pending_word: string =
    BigInt(myByteArray.pending_word) === 0n
      ? ''
      : decodeShortString(toHex(myByteArray.pending_word));
  return (
    myByteArray.data.reduce<string>((cumuledString, encodedString: BigNumberish) => {
      const add: string =
        BigInt(encodedString) === 0n ? '' : decodeShortString(toHex(encodedString));
      return cumuledString + add;
    }, '') + pending_word
  );
}

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
export function byteArrayFromString(targetString: string): ByteArray {
  const shortStrings: string[] = splitLongString(targetString);
  const remainder: string = shortStrings[shortStrings.length - 1];
  const shortStringsEncoded: BigNumberish[] = shortStrings.map(encodeShortString);

  const [pendingWord, pendingWordLength] =
    remainder === undefined || remainder.length === 31
      ? ['0x00', 0]
      : [shortStringsEncoded.pop()!, remainder.length];

  return {
    data: shortStringsEncoded.length === 0 ? [] : shortStringsEncoded,
    pending_word: pendingWord,
    pending_word_len: pendingWordLength,
  };
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/byteArray.ts`.

**Functions defined**: stringFromByteArray, byteArrayFromString

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 59
- Comment lines: 29
- Blank lines: -24

### Main Components

**Functions** (2):
- `byteArrayFromString()`
- `stringFromByteArray()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../num.js` (imported)
- `../shortString.js` (imported)
- `../../types/lib/index.js` (imported)
- `../num.js` (referenced)
- `../shortString.js` (referenced)
- `../../types/lib/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/utils/calldata/byteArray.ts
```

