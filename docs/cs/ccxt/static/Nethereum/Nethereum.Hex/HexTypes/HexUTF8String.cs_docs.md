# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexUTF8String.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexUTF8String.cs`
- **Size**: 570 bytes
- **Lines**: 22
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.Hex.HexConvertors;
using Newtonsoft.Json;

namespace Nethereum.Hex.HexTypes
{
    [JsonConverter(typeof(HexRPCTypeJsonConverter<HexUTF8String, string>))]
    public class HexUTF8String : HexRPCType<string>
    {
        private HexUTF8String() : base(new HexUTF8StringConvertor())
        {
        }

        public HexUTF8String(string value) : base(value, new HexUTF8StringConvertor())
        {
        }

        public static HexUTF8String CreateFromHex(string hex)
        {
            return new HexUTF8String {HexValue = hex};
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/HexTypes/HexUTF8String.cs`.

**Classes defined**: HexUTF8String



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 19
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `HexUTF8String`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

