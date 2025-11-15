# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/ICipherBuilderWithKey.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/ICipherBuilderWithKey.cs`
- **Size**: 389 bytes
- **Lines**: 17
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// A cipher builder that can also return the key it was initialized with.
    /// </summary>
    public interface ICipherBuilderWithKey
        : ICipherBuilder
    {
        /// <summary>
        /// Return the key we were initialized with.
        /// </summary>
        ICipherParameters Key { get; }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/ICipherBuilderWithKey.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 9
- Comment lines: 6
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

