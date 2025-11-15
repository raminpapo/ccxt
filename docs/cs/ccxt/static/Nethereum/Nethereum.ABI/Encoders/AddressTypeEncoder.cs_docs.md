# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/AddressTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/AddressTypeEncoder.cs`
- **Size**: 1,475 bytes
- **Lines**: 50
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.ABI.Encoders
{
    public class AddressTypeEncoder : ITypeEncoder
    {
        private readonly IntTypeEncoder _intTypeEncoder;

        public AddressTypeEncoder()
        {
            _intTypeEncoder = new IntTypeEncoder();
        }

        public byte[] Encode(object value)
        {
            var strValue = value as string;

            if ((strValue != null)
                && !strValue.StartsWith("0x", StringComparison.Ordinal))
                value = "0x" + value;

            var addr = _intTypeEncoder.Encode(value);

            for (var i = 0; i < 12; i++)
            {
                if ((addr[i] != 0) && (addr[i] != 0xFF))
                    throw new Exception("Invalid address (should be 20 bytes length): " + addr.ToHex());

                if (addr[i] == 0xFF) addr[i] = 0;
            }
            return addr;
        }

        public byte[] EncodePacked(object value)
        {
            var strValue = value as string;

            if(strValue == null) throw new Exception("Invalid type for address expected as string");

            if ((strValue != null)
                && !strValue.StartsWith("0x", StringComparison.Ordinal))
                value = "0x" + value;

            if (strValue.Length == 42) return strValue.HexToByteArray();

            throw new Exception("Invalid address (should be 20 bytes length): " + strValue);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/AddressTypeEncoder.cs`.

**Classes defined**: AddressTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 38
- Comment lines: 0
- Blank lines: 12

### Main Components

**Classes** (1):
- `AddressTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

