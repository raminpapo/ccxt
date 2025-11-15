# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/AttributeEncoding/ParameterOutputProperty.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/AttributeEncoding/ParameterOutputProperty.cs`
- **Size**: 327 bytes
- **Lines**: 12
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Collections.Generic;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.AttributeEncoding
{
    public class ParameterOutputProperty : ParameterOutput
    {
        public PropertyInfo PropertyInfo { get; set; }

        public List<ParameterOutputProperty> ChildrenProperties { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/AttributeEncoding/ParameterOutputProperty.cs`.

**Classes defined**: ParameterOutputProperty



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 10
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `ParameterOutputProperty`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

