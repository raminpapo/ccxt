# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexTypeFactory.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexTypeFactory.cs`
- **Size**: 738 bytes
- **Lines**: 27
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Numerics;

namespace Nethereum.Hex.HexTypes
{
    public class HexTypeFactory
    {
        public static object CreateFromHex<T>(string hex)
        {
            if (typeof(BigInteger) == typeof(T))
                return new HexBigInteger(hex);

            if (typeof(string) == typeof(T))
                return HexUTF8String.CreateFromHex(hex);
            throw new NotImplementedException();
        }

        public static object CreateFromObject<T>(object value)
        {
            if (value == null) return null; // if null
            if (typeof(BigInteger) == typeof(T))
                return new HexBigInteger((long) value);

            throw new NotImplementedException();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexTypeFactory.cs`.

**Classes defined**: HexTypeFactory



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 23
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `HexTypeFactory`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

