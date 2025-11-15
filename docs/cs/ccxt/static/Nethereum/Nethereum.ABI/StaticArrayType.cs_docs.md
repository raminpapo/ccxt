# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/StaticArrayType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/StaticArrayType.cs`
- **Size**: 1,005 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class StaticArrayType : ArrayType
    {
        internal int Size;

        public StaticArrayType(string name) : base(name)
        {
            IntialiseSize(name);
            Decoder = new ArrayTypeDecoder(ElementType, Size);
            Encoder = new StaticArrayTypeEncoder(ElementType, Size);
        }

        public override string CanonicalName => ElementType.CanonicalName + "[" + Size + "]";

        public override int FixedSize => ElementType.FixedSize * Size;

        private void IntialiseSize(string name)
        {
            var indexFirstBracket = name.LastIndexOf("[", StringComparison.Ordinal);
            var indexSecondBracket = name.IndexOf("]", indexFirstBracket, StringComparison.Ordinal);
            var arraySize = name.Substring(indexFirstBracket + 1, indexSecondBracket - (indexFirstBracket + 1));
            Size = int.Parse(arraySize);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/StaticArrayType.cs`.

**Classes defined**: StaticArrayType



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 25
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `StaticArrayType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

