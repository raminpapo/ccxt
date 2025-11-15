# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/StringTypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/StringTypeDecoder.cs`
- **Size**: 789 bytes
- **Lines**: 29
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Text;

namespace Nethereum.ABI.Decoders
{
    public class StringTypeDecoder : TypeDecoder
    {
        public override object Decode(byte[] encoded, Type type)
        {
            if (!IsSupportedType(type)) throw new NotSupportedException(type + " is not supported");
            return Encoding.UTF8.GetString(encoded, 32, EncoderDecoderHelpers.GetNumberOfBytes(encoded));
        }

        public string Decode(byte[] encoded)
        {
            return Decode<string>(encoded);
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

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/StringTypeDecoder.cs`.

**Classes defined**: StringTypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 25
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `StringTypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

