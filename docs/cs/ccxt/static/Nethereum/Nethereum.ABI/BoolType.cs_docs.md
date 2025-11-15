# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/BoolType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/BoolType.cs`
- **Size**: 287 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class BoolType : ABIType
    {
        public BoolType() : base("bool")
        {
            Decoder = new BoolTypeDecoder();
            Encoder = new BoolTypeEncoder();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/BoolType.cs`.

**Classes defined**: BoolType



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 13
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `BoolType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

