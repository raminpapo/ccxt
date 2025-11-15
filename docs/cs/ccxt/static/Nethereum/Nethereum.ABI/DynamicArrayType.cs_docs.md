# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/DynamicArrayType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/DynamicArrayType.cs`
- **Size**: 481 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class DynamicArrayType : ArrayType
    {
        public DynamicArrayType(string name) : base(name)
        {
            Decoder = new DynamicArrayTypeDecoder(ElementType);
            Encoder = new DynamicArrayTypeEncoder(ElementType);
        }

        public override string CanonicalName => ElementType.CanonicalName + "[]";

        public override int FixedSize => -1;
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/DynamicArrayType.cs`.

**Classes defined**: DynamicArrayType



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `DynamicArrayType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

