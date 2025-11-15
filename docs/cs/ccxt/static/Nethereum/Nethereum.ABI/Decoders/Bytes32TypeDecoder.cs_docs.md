# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/Bytes32TypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/Bytes32TypeDecoder.cs`
- **Size**: 1,595 bytes
- **Lines**: 52
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Text;

namespace Nethereum.ABI.Decoders
{
    public class Bytes32TypeDecoder : TypeDecoder
    {
        private readonly BoolTypeDecoder _boolTypeDecoder;
        private readonly IntTypeDecoder _intTypeDecoder;

        public Bytes32TypeDecoder()
        {
            _intTypeDecoder = new IntTypeDecoder();
            _boolTypeDecoder = new BoolTypeDecoder();
        }

        public override object Decode(byte[] encoded, Type type)
        {
            if (!IsSupportedType(type)) throw new NotSupportedException(type + " is not supported");

            if (type == typeof(byte[]) || type == typeof(object))
                return encoded;

            if (type == typeof(string))
                return DecodeString(encoded);

            if (_intTypeDecoder.IsSupportedType(type))
                return _intTypeDecoder.Decode(encoded, type);

            if (_boolTypeDecoder.IsSupportedType(type))
                return _boolTypeDecoder.Decode(encoded, type);

            throw new NotSupportedException();
        }

        public override Type GetDefaultDecodingType()
        {
            return typeof(byte[]);
        }

        public override bool IsSupportedType(Type type)
        {
            return type == typeof(byte[]) || type == typeof(string) || _intTypeDecoder.IsSupportedType(type)
                   || type == typeof(bool) || type == typeof(object);
        }

        private string DecodeString(byte[] encoded)
        {
            return Encoding.UTF8.GetString(encoded, 0, encoded.Length).TrimEnd('\0');
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/Bytes32TypeDecoder.cs`.

**Classes defined**: Bytes32TypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 41
- Comment lines: 0
- Blank lines: 11

### Main Components

**Classes** (1):
- `Bytes32TypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

