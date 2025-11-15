# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IStreamCalculator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IStreamCalculator.cs`
- **Size**: 813 bytes
- **Lines**: 24
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.IO;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Base interface for cryptographic operations such as Hashes, MACs, and Signatures which reduce a stream of data
    /// to a single value.
    /// </summary>
    public interface IStreamCalculator
    {
        /// <summary>Return a "sink" stream which only exists to update the implementing object.</summary>
        /// <returns>A stream to write to in order to update the implementing object.</returns>
        Stream Stream { get; }

        /// <summary>
        /// Return the result of processing the stream. This value is only available once the stream
        /// has been closed.
        /// </summary>
        /// <returns>The result of processing the stream.</returns>
        object GetResult();
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IStreamCalculator.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 10
- Comment lines: 11
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

