# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/BytesType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/BytesType.cs`
- **Size**: 338 bytes
- **Lines**: 16
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class BytesType : ABIType
    {
        public BytesType() : base("bytes")
        {
            Decoder = new BytesTypeDecoder();
            Encoder = new BytesTypeEncoder();
        }

        public override int FixedSize => -1;
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/BytesType.cs`.

**Classes defined**: BytesType



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 14
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `BytesType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
