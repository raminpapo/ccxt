# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ITypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ITypeDecoder.cs`
- **Size**: 358 bytes
- **Lines**: 17
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Nethereum.ABI.Decoders
{
    public interface ITypeDecoder
    {
        object Decode(byte[] encoded, Type type);

        T Decode<T>(byte[] encoded);

        object Decode(string hexString, Type type);

        T Decode<T>(string hexString);
        Type GetDefaultDecodingType();
        bool IsSupportedType(Type type);
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ITypeDecoder.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

