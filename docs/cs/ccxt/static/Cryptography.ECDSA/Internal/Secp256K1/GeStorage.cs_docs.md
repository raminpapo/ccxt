# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/GeStorage.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/GeStorage.cs`
- **Size**: 265 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿namespace Cryptography.ECDSA.Internal.Secp256K1
{
    internal class GeStorage
    {
        public FeStorage X;
        public FeStorage Y;

        public GeStorage()
        {
            X = new FeStorage();
            Y = new FeStorage();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/GeStorage.cs`.

**Classes defined**: GeStorage



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 13
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `GeStorage`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

