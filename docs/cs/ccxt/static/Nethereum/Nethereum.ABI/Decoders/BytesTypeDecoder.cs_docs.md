# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BytesTypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BytesTypeDecoder.cs`
- **Size**: 1,112 bytes
- **Lines**: 35
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Linq;

namespace Nethereum.ABI.Decoders
{
    public class BytesTypeDecoder : TypeDecoder
    {
        private readonly StringTypeDecoder _stringTypeDecoder;

        public BytesTypeDecoder()
        {
            _stringTypeDecoder = new StringTypeDecoder();
        }

        public override object Decode(byte[] encoded, Type type)
        {
            if (!IsSupportedType(type)) throw new NotSupportedException(type + " is not supported");
            if (type == typeof(string)) return _stringTypeDecoder.Decode(encoded, type);
            var returnArray = encoded.Skip(32).Take(EncoderDecoderHelpers.GetNumberOfBytes(encoded)).ToArray();
            if (type == typeof(byte)) return returnArray[0];
            return returnArray;
        }

        public override Type GetDefaultDecodingType()
        {
            return typeof(byte[]);
        }

        public override bool IsSupportedType(Type type)
        {
            return type == typeof(string) || type == typeof(byte[]) || type == typeof(object)
                   || type == typeof(byte);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BytesTypeDecoder.cs`.

**Classes defined**: BytesTypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 30
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `BytesTypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
