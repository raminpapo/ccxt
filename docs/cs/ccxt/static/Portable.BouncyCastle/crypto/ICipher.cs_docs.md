# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/ICipher.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/ICipher.cs`
- **Size**: 1,778 bytes
- **Lines**: 42
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.IO;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Base interface for a ciphers that do not require data to be block aligned.
    /// <para>
    /// Note: In cases where the underlying algorithm is block based, these ciphers may add or remove padding as needed.
    /// </para>
    /// </summary>
    public interface ICipher
    {
        /// <summary>
        /// Return the size of the output buffer required for a Write() plus a
        /// close() with the write() being passed inputLen bytes.
        /// <para>
        /// The returned size may be dependent on the initialisation of this cipher
        /// and may not be accurate once subsequent input data is processed as the cipher may
        /// add, add or remove padding, as it sees fit.
        /// </para>
        /// </summary>
        /// <returns>The space required to accommodate a call to processBytes and doFinal with inputLen bytes of input.</returns>
        /// <param name="inputLen">The length of the expected input.</param>
        int GetMaxOutputSize(int inputLen);

        /// <summary>
        /// Return the size of the output buffer required for a write() with the write() being
        /// passed inputLen bytes and just updating the cipher output.
        /// </summary>
        /// <returns>The space required to accommodate a call to processBytes with inputLen bytes of input.</returns>
        /// <param name="inputLen">The length of the expected input.</param>
        int GetUpdateOutputSize(int inputLen);

        /// <summary>
        /// Gets the stream for reading/writing data processed/to be processed.
        /// </summary>
        /// <value>The stream associated with this cipher.</value>
        Stream Stream { get; }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/ICipher.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 11
- Comment lines: 27
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

