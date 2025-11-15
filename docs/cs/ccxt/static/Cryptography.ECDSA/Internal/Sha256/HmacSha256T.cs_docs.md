# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Sha256/HmacSha256T.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Sha256/HmacSha256T.cs`
- **Size**: 274 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿namespace Cryptography.ECDSA.Internal.Sha256
{
    internal class HmacSha256T
    {
        public Sha256T Inner;
        public Sha256T Outer;

        public HmacSha256T()
        {
            Inner = new Sha256T();
            Outer = new Sha256T();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Sha256/HmacSha256T.cs`.

**Classes defined**: HmacSha256T



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 13
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `HmacSha256T`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

