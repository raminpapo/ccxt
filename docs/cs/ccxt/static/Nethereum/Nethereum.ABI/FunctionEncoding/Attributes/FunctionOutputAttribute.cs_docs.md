# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/FunctionOutputAttribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/FunctionOutputAttribute.cs`
- **Size**: 529 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    [AttributeUsage(AttributeTargets.Class)]
    public class FunctionOutputAttribute : Attribute
    {
        public static FunctionOutputAttribute GetAttribute<T>()
        {
            var type = typeof(T);
            return type.GetTypeInfo().GetCustomAttribute<FunctionOutputAttribute>(true);
        }

        public static bool IsFunctionType<T>()
        {
            return GetAttribute<T>() != null;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/FunctionOutputAttribute.cs`.

**Classes defined**: FunctionOutputAttribute



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 18
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `FunctionOutputAttribute`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

