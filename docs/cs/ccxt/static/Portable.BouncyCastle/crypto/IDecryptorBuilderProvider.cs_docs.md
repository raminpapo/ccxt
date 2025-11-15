# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IDecryptorBuilderProvider.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IDecryptorBuilderProvider.cs`
- **Size**: 599 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Interface describing a provider of cipher builders for creating decrypting ciphers.
    /// </summary>
    public interface IDecryptorBuilderProvider
	{
        /// <summary>
        /// Return a cipher builder for creating decrypting ciphers.
        /// </summary>
        /// <param name="algorithmDetails">The algorithm details/parameters to use to create the final cipher.</param>
        /// <returns>A new cipher builder.</returns>
        ICipherBuilder CreateDecryptorBuilder(object algorithmDetails);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IDecryptorBuilderProvider.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 8
- Comment lines: 8
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

