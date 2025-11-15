# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexBigIntegerNumberExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexBigIntegerNumberExtensions.cs`
- **Size**: 645 bytes
- **Lines**: 27
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Numerics;

namespace Nethereum.Hex.HexTypes
{
    public static class HexBigIntegerNumberExtensions
    {
        public static HexBigInteger ToHexBigInteger(this ulong val)
        {
            return new HexBigInteger(val);
        }

        public static HexBigInteger ToHexBigInteger(this int val)
        {
            return new HexBigInteger(val);
        }

        public static HexBigInteger ToHexBigInteger(this BigInteger val)
        {
            return new HexBigInteger(val);
        }

        public static ulong ToUlong(this HexBigInteger val)
        {
            return (ulong)val.Value;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexBigIntegerNumberExtensions.cs`.

**Classes defined**: HexBigIntegerNumberExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 23
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `HexBigIntegerNumberExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

