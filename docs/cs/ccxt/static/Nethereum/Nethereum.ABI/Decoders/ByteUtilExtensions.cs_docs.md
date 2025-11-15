# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ByteUtilExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ByteUtilExtensions.cs`
- **Size**: 608 bytes
- **Lines**: 25
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Numerics;

namespace Nethereum.ABI.Decoders
{
    public static class ByteUtilExtensions
    {
        public static BigInteger ConvertToInt256(this byte[] bytes)
        {
            var value = new IntType("int256").Decode<BigInteger>(bytes);

            if (value > IntType.MAX_INT256_VALUE)
            {
                value = 1 + IntType.MAX_UINT256_VALUE - value;
            }

            return value;
        }

        public static BigInteger ConvertToUInt256(this byte[] bytes)
        {
            return new IntType("uint256").Decode<BigInteger>(bytes);
        }

    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ByteUtilExtensions.cs`.

**Classes defined**: ByteUtilExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 20
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `ByteUtilExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

