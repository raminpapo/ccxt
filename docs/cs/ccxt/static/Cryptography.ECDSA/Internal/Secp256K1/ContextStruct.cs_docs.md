# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/ContextStruct.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/ContextStruct.cs`
- **Size**: 454 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Cryptography.ECDSA.Internal.Secp256K1
{
    internal class ContextStruct
    {
        public EcMultContext EcMultCtx;
        public EcmultGenContext EcMultGenCtx;
        public EventHandler<Callback> IllegalCallback;
        public EventHandler<Callback> ErrorCallback;

        public ContextStruct()
        {
            EcMultCtx = new EcMultContext();
            EcMultGenCtx = new EcmultGenContext();
        }
    };
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/ContextStruct.cs`.

**Classes defined**: ContextStruct



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 16
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `ContextStruct`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

