# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/TypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/TypeDecoder.cs`
- **Size**: 793 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.ABI.Decoders
{
    public abstract class TypeDecoder : ITypeDecoder
    {
        public abstract bool IsSupportedType(Type type);
        public abstract object Decode(byte[] encoded, Type type);

        public T Decode<T>(byte[] encoded)
        {
            return (T) Decode(encoded, typeof(T));
        }

        public object Decode(string encoded, Type type)
        {
            if (!encoded.StartsWith("0x"))
                encoded = "0x" + encoded;

            return Decode(encoded.HexToByteArray(), type);
        }

        public T Decode<T>(string encoded)
        {
            return (T) Decode(encoded, typeof(T));
        }

        public abstract Type GetDefaultDecodingType();
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/TypeDecoder.cs`.

**Classes defined**: TypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 25
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `TypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

