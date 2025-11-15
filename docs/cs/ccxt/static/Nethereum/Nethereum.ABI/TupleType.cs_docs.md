# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/TupleType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/TupleType.cs`
- **Size**: 1,221 bytes
- **Lines**: 43
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Linq;
using Nethereum.ABI.Model;
using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.ABI
{
    public class TupleType : ABIType
    {
        public Parameter[] Components { get; protected set; }

        public void SetComponents(Parameter[] components)
        {
            this.Components = components;
            ((TupleTypeEncoder) Encoder).Components = components;
            ((TupleTypeDecoder) Decoder).Components = components;
        }

        public TupleType() : base("tuple")
        {
            Decoder = new TupleTypeDecoder();
            Encoder = new TupleTypeEncoder();
        }

        public T DecodeComplexType<T>(string encoded)
        {
            return DecodeComplexType<T>(encoded.HexToByteArray());
        }

        public T DecodeComplexType<T>(byte[] encoded)
        {
            return ((TupleTypeDecoder)Decoder).DecodeComplexType<T>(encoded);
        }

        public override int FixedSize {
            get
            {
                if (Components == null) return -1;
                if (Components.Any(x => x.ABIType.IsDynamic())) return -1;
                return Components.Sum(x => x.ABIType.FixedSize);
            }
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/TupleType.cs`.

**Classes defined**: TupleType



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 37
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `TupleType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

