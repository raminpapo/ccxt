# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/HexBigIntegerBigEndianConvertor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/HexBigIntegerBigEndianConvertor.cs`
- **Size**: 439 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Numerics;
using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.Hex.HexConvertors
{
    public class HexBigIntegerBigEndianConvertor : IHexConvertor<BigInteger>
    {
        public string ConvertToHex(BigInteger newValue)
        {
            return newValue.ToHex(false);
        }

        public BigInteger ConvertFromHex(string hex)
        {
            return hex.HexToBigInteger(false);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/HexBigIntegerBigEndianConvertor.cs`.

**Classes defined**: HexBigIntegerBigEndianConvertor



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 16
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `HexBigIntegerBigEndianConvertor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

