# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Options.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Options.cs`
- **Size**: 956 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Cryptography.ECDSA.Internal.Secp256K1
{
    [Flags]
    internal enum Options : uint
    {
        // All flags' lower 8 bits indicate what they're for. Do not use directly.
        FlagsTypeMask = ((1 << 8) - 1),
        FlagsTypeContext = (1 << 0),
        FlagsTypeCompression = (1 << 1),
        // The higher bits contain the actual data. Do not use directly. 
        FlagsBitContextVerify = (1 << 8),
        FlagsBitContextSign = (1 << 9),
        FlagsBitCompression = (1 << 8),

        /** Flags to pass to secp256k1_context_create. */
        ContextVerify = (FlagsTypeContext | FlagsBitContextVerify),
        ContextSign = (FlagsTypeContext | FlagsBitContextSign),
        ContextNone = (FlagsTypeContext),

        /** Flag to pass to EcPubkeySerialize and secp256k1_ec_privkey_export. */
        EcCompressed = (FlagsTypeCompression | FlagsBitCompression),
        EcUncompressed = (FlagsTypeCompression)
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Options.cs`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 21
- Comment lines: 4
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

