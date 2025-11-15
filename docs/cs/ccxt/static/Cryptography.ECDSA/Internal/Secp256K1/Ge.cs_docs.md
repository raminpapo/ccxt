# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Ge.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Ge.cs`
- **Size**: 554 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Cryptography.ECDSA.Internal.Secp256K1
{
    /// <summary>
    /// A group element of the secp256k1 curve, in affine coordinates.
    /// </summary>
    internal class Ge
    {
        public Fe X;
        public Fe Y;
        public bool Infinity; // whether this represents the point at infinity

        public Ge()
        {
            X = new Fe();
            Y = new Fe();
        }

        public Ge(UInt32[] xarr, UInt32[] yarr)
        {
            X = new Fe(xarr);
            Y = new Fe(yarr);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Ge.cs`.

**Classes defined**: Ge



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 20
- Comment lines: 3
- Blank lines: 3

### Main Components

**Classes** (1):
- `Ge`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

