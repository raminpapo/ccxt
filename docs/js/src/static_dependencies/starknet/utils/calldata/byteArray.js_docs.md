# Documentation: js/src/static_dependencies/starknet/utils/calldata/byteArray.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/byteArray.js`
- **Size**: 1,853 bytes
- **Lines**: 54
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
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
export function stringFromByteArray(myByteArray) {
    const pending_word = BigInt(myByteArray.pending_word) === 0n
        ? ''
        : decodeShortString(toHex(myByteArray.pending_word));
    return (myByteArray.data.reduce((cumuledString, encodedString) => {
        const add = BigInt(encodedString) === 0n ? '' : decodeShortString(toHex(encodedString));
        return cumuledString + add;
    }, '') + pending_word);
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
export function byteArrayFromString(targetString) {
    const shortStrings = splitLongString(targetString);
    const remainder = shortStrings[shortStrings.length - 1];
    const shortStringsEncoded = shortStrings.map(encodeShortString);
    const [pendingWord, pendingWordLength] = remainder === undefined || remainder.length === 31
        ? ['0x00', 0]
        : [shortStringsEncoded.pop(), remainder.length];
    return {
        data: shortStringsEncoded.length === 0 ? [] : shortStringsEncoded,
        pending_word: pendingWord,
        pending_word_len: pendingWordLength,
    };
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/byteArray.js`.

**Functions defined**: stringFromByteArray, byteArrayFromString

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 53
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

- `../num.js` (imported)
- `../shortString.js` (imported)
- `../num.js` (referenced)
- `../shortString.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/byteArray.js
```

