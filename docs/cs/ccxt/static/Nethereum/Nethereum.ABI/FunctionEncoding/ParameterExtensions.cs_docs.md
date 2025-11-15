# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ParameterExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ParameterExtensions.cs`
- **Size**: 390 bytes
- **Lines**: 13
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.Model;

namespace Nethereum.ABI.FunctionEncoding
{
    public static class ParameterExtensions
    {
        public static string GetParameterNameUsingDefaultIfNotSet(this Parameter parameter)
        {
            if(!string.IsNullOrEmpty(parameter.Name)) return parameter.Name;
            return "param_" + parameter.Order + "_" + parameter.Type;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ParameterExtensions.cs`.

**Classes defined**: ParameterExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 12
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `ParameterExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

