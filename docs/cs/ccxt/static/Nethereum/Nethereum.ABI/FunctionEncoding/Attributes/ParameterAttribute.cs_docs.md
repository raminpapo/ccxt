# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterAttribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterAttribute.cs`
- **Size**: 1,103 bytes
- **Lines**: 35
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Nethereum.ABI.Model;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    [AttributeUsage(AttributeTargets.Property)]
    public class ParameterAttribute : Attribute
    {
        public ParameterAttribute(string type, string name = null, int order = 1)
        {
            Parameter = new Parameter(type, name, order);
        }

        public ParameterAttribute(string type, string name, int order, bool indexed = false) : this(type, name, order)
        {
            Parameter.Indexed = indexed;
        }

        public ParameterAttribute(string type, string name, int order, string structTypeName = null) : this(type, name, order)
        {
            Parameter.StructTypeName = structTypeName;
        }

        public ParameterAttribute(string type, int order) : this(type, null, order)
        {
        }

        public Parameter Parameter { get; }

        public int Order => Parameter.Order;
        public string Name => Parameter.Name;
        public string Type => Parameter.Type;
        public string StructTypeName => Parameter.StructTypeName;
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterAttribute.cs`.

**Classes defined**: ParameterAttribute



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 29
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `ParameterAttribute`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

