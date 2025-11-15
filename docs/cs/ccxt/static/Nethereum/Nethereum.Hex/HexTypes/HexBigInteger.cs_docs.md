# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexBigInteger.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexBigInteger.cs`
- **Size**: 622 bytes
- **Lines**: 25
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Numerics;
using Nethereum.Hex.HexConvertors;
using Newtonsoft.Json;

namespace Nethereum.Hex.HexTypes
{
    [JsonConverter(typeof(HexRPCTypeJsonConverter<HexBigInteger, BigInteger>))]
    public class HexBigInteger : HexRPCType<BigInteger>
    {
        public HexBigInteger(string hex) : base(new HexBigIntegerBigEndianConvertor(), hex)
        {
        }

        public HexBigInteger(BigInteger value) : base(value, new HexBigIntegerBigEndianConvertor())
        {
        }

        
        public override string ToString()
        {
            return Value.ToString();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexBigInteger.cs`.

**Classes defined**: HexBigInteger



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 21
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `HexBigInteger`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

