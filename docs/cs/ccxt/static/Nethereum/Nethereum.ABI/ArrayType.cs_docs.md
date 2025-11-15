# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/ArrayType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/ArrayType.cs`
- **Size**: 1,228 bytes
- **Lines**: 34
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Nethereum.ABI
{
    public abstract class ArrayType : ABIType
    {
        public ABIType ElementType { get; set; }

        protected ArrayType(string name) : base(name)
        {
            InitialiseElementType(name);
        }

        public new static ArrayType CreateABIType(string typeName)
        {
            var indexFirstBracket = typeName.LastIndexOf("[", StringComparison.Ordinal);
            var indexSecondBracket = typeName.IndexOf("]", indexFirstBracket, StringComparison.Ordinal);

            if (indexFirstBracket + 1 == indexSecondBracket)
                return new DynamicArrayType(typeName);
            return new StaticArrayType(typeName);
        }

        private void InitialiseElementType(string name)
        {
            var indexLastBracket = name.LastIndexOf("[", StringComparison.Ordinal);
            var elementTypeName = name.Substring(0, indexLastBracket);
            //var indexSecondBracket = name.IndexOf("]", indexFirstBracket, StringComparison.Ordinal);

            //var subDim = indexSecondBracket + 1 == name.Length ? "" : name.Substring(indexSecondBracket + 1);
            ElementType = ABIType.CreateABIType(elementTypeName);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/ArrayType.cs`.

**Classes defined**: ArrayType



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 26
- Comment lines: 2
- Blank lines: 6

### Main Components

**Classes** (1):
- `ArrayType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

