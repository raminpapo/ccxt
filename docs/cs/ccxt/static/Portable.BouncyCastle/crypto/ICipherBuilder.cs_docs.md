# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/ICipherBuilder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/ICipherBuilder.cs`
- **Size**: 1,053 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Base interface for cipher builders.
    /// </summary>
    public interface ICipherBuilder
    {
        /// <summary>
        /// Return the algorithm and parameter details associated with any cipher built.
        /// </summary>
        object AlgorithmDetails { get; }

        /// <summary>
        /// Return the maximum output size that a given input will produce.
        /// </summary>
        /// <param name="inputLen">the length of the expected input.</param>
        /// <returns>The maximum possible output size that can produced for the expected input length.</returns>
        int GetMaxOutputSize(int inputLen);

        /// <summary>
        /// Build a cipher that operates on the passed in stream.
        /// </summary>
        /// <param name="stream">The stream to write/read any encrypted/decrypted data.</param>
        /// <returns>A cipher based around the given stream.</returns>
        ICipher BuildCipher(Stream stream);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/ICipherBuilder.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 11
- Comment lines: 16
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

