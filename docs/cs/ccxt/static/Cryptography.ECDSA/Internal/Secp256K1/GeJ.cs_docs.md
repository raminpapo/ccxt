# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/GeJ.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/GeJ.cs`
- **Size**: 781 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿namespace Cryptography.ECDSA.Internal.Secp256K1
{
    /// <summary>
    /// A group element of the secp256k1 curve, in jacobian coordinates.
    /// </summary>
    internal class GeJ
    {
        public Fe X; // actual X: x/z^2 
        public Fe Y; // actual Y: y/z^3
        public Fe Z;
        public bool Infinity; // whether this represents the point at infinity

        public GeJ()
        {
            X = new Fe();
            Y = new Fe();
            Z = new Fe();
        }

        public GeJ(Fe xVal, Fe yVal, Fe zVal)
        {
            X = xVal ?? new Fe();
            Y = yVal ?? new Fe();
            Z = zVal ?? new Fe();
        }

        public GeJ Clone()
        {
            return new GeJ(X?.Clone(), Y?.Clone(), Z?.Clone());
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/GeJ.cs`.

**Classes defined**: GeJ



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 26
- Comment lines: 3
- Blank lines: 3

### Main Components

**Classes** (1):
- `GeJ`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

