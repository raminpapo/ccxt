# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/StringType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/StringType.cs`
- **Size**: 343 bytes
- **Lines**: 16
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class StringType : ABIType
    {
        public StringType() : base("string")
        {
            Decoder = new StringTypeDecoder();
            Encoder = new StringTypeEncoder();
        }

        public override int FixedSize => -1;
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/StringType.cs`.

**Classes defined**: StringType



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 14
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `StringType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

