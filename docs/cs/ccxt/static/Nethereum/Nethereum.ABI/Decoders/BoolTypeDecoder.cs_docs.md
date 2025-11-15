# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BoolTypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BoolTypeDecoder.cs`
- **Size**: 927 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Nethereum.ABI.Decoders
{
    public class BoolTypeDecoder : TypeDecoder
    {
        private readonly IntTypeDecoder _intTypeDecoder;

        public BoolTypeDecoder()
        {
            _intTypeDecoder = new IntTypeDecoder();
        }

        public bool Decode(byte[] encoded)
        {
            return Decode<bool>(encoded);
        }

        public override object Decode(byte[] encoded, Type type)
        {
            if (!IsSupportedType(type)) throw new NotSupportedException(type + " is not supported");
            var decoded = _intTypeDecoder.DecodeInt(encoded);
            return Convert.ToBoolean(decoded);
        }

        public override Type GetDefaultDecodingType()
        {
            return typeof(bool);
        }

        public override bool IsSupportedType(Type type)
        {
            return type == typeof(bool) || type == typeof(object);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BoolTypeDecoder.cs`.

**Classes defined**: BoolTypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 30
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `BoolTypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

