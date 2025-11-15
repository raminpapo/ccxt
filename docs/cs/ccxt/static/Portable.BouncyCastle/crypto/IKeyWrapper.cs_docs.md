# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IKeyWrapper.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IKeyWrapper.cs`
- **Size**: 612 bytes
- **Lines**: 23
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Base interface for a key wrapper.
    /// </summary>
    public interface IKeyWrapper
    {
        /// <summary>
        /// The parameter set used to configure this key wrapper.
        /// </summary>
        object AlgorithmDetails { get; }

        /// <summary>
        /// Wrap the passed in key data.
        /// </summary>
        /// <param name="keyData">The key data to be wrapped.</param>
        /// <returns>an IBlockResult containing the wrapped key data.</returns>
        IBlockResult Wrap(byte[] keyData);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IKeyWrapper.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 9
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

