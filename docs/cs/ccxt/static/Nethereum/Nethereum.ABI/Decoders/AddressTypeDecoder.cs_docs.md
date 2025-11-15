# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/AddressTypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/AddressTypeDecoder.cs`
- **Size**: 946 bytes
- **Lines**: 34
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Nethereum.Hex.HexConvertors.Extensions;
using Nethereum.Util;

namespace Nethereum.ABI.Decoders
{
    public class AddressTypeDecoder : TypeDecoder
    {
        private IntTypeDecoder _intTypeDecoder;

        public AddressTypeDecoder()
        {
            _intTypeDecoder = new IntTypeDecoder();
        }

        public override object Decode(byte[] encoded, Type type)
        {
            if (!IsSupportedType(type)) throw new NotSupportedException(type + " is not supported");
            var output = new byte[20];
            Array.Copy(encoded, 12, output, 0, 20);
            return output.ToHex(true).ConvertToEthereumChecksumAddress();
        }

        public override Type GetDefaultDecodingType()
        {
            return typeof(string);
        }

        public override bool IsSupportedType(Type type)
        {
            return type == typeof(string) || type == typeof(object);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/AddressTypeDecoder.cs`.

**Classes defined**: AddressTypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 29
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `AddressTypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

