# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/Extensions/HexStringUTF8ConvertorExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/Extensions/HexStringUTF8ConvertorExtensions.cs`
- **Size**: 482 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Text;

namespace Nethereum.Hex.HexConvertors.Extensions
{
    public static class HexStringUTF8ConvertorExtensions
    {
        public static string ToHexUTF8(this string value)
        {
            return "0x" + Encoding.UTF8.GetBytes(value).ToHex();
        }


        public static string HexToUTF8String(this string hex)
        {
            var bytes = hex.HexToByteArray();
            return Encoding.UTF8.GetString(bytes, 0, bytes.Length);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexConvertors/Extensions/HexStringUTF8ConvertorExtensions.cs`.

**Classes defined**: HexStringUTF8ConvertorExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 16
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `HexStringUTF8ConvertorExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

