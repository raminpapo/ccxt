# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/HexUTF8StringConvertor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/HexUTF8StringConvertor.cs`
- **Size**: 383 bytes
- **Lines**: 17
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.Hex.HexConvertors
{
    public class HexUTF8StringConvertor : IHexConvertor<string>
    {
        public string ConvertToHex(string value)
        {
            return value.ToHexUTF8();
        }

        public string ConvertFromHex(string hex)
        {
            return hex.HexToUTF8String();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/HexUTF8StringConvertor.cs`.

**Classes defined**: HexUTF8StringConvertor



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 15
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `HexUTF8StringConvertor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

