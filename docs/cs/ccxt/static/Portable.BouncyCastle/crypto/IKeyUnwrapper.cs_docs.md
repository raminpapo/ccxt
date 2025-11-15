# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IKeyUnwrapper.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IKeyUnwrapper.cs`
- **Size**: 851 bytes
- **Lines**: 25
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Base interface for a key unwrapper.
    /// </summary>
    public interface IKeyUnwrapper
    {
        /// <summary>
        /// The parameter set used to configure this key unwrapper.
        /// </summary>
        object AlgorithmDetails { get; }

        /// <summary>
        /// Unwrap the passed in data.
        /// </summary>
        /// <param name="cipherText">The array containing the data to be unwrapped.</param>
        /// <param name="offset">The offset into cipherText at which the unwrapped data starts.</param>
        /// <param name="length">The length of the data to be unwrapped.</param>
        /// <returns>an IBlockResult containing the unwrapped key data.</returns>
        IBlockResult Unwrap(byte[] cipherText, int offset, int length);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IKeyUnwrapper.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 9
- Comment lines: 13
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

