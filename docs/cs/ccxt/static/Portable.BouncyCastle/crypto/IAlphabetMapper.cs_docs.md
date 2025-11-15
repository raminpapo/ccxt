# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IAlphabetMapper.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IAlphabetMapper.cs`
- **Size**: 952 bytes
- **Lines**: 33
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
/**
 * Base interface for mapping from an alphabet to a set of indexes
 * suitable for use with FPE.
 */
public interface IAlphabetMapper
{
    /// <summary>
    /// Return the number of characters in the alphabet.
    /// </summary>
    /// <returns>the radix for the alphabet.</returns>
    int Radix { get; }

    /// <summary>
    /// Return the passed in char[] as a byte array of indexes (indexes
    /// can be more than 1 byte)
    /// </summary>
    /// <returns>an index array.</returns>
    /// <param name="input">characters to be mapped.</param>   
    byte[] ConvertToIndexes(char[] input);

    /// <summary>
    /// Return a char[] for this alphabet based on the indexes passed.
    /// </summary>
    /// <returns>an array of char corresponding to the index values.</returns>
    /// <param name="input">input array of indexes.</param>   
    char[] ConvertToChars(byte[] input);
}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IAlphabetMapper.cs`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 14
- Comment lines: 19
- Blank lines: 0

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

