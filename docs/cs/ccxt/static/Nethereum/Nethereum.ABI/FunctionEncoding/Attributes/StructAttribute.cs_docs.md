# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/StructAttribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/StructAttribute.cs`
- **Size**: 1,179 bytes
- **Lines**: 48
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    [AttributeUsage(AttributeTargets.Class)]
    public class StructAttribute : Attribute
    {
        public StructAttribute(string name)
        {
            this.Name = name;
        }

        public string Name { get; set; }
      
        public static StructAttribute GetAttribute<T>()
        {
            var type = typeof(T);
            return GetAttribute(type);
        }

        public static StructAttribute GetAttribute(Type type)
        {
            return type.GetTypeInfo().GetCustomAttribute<StructAttribute>(true);
        }

        public static StructAttribute GetAttribute(object instance)
        {
            var type = instance.GetType();
            return GetAttribute(type);
        }

        public static bool IsStructType<T>()
        {
            return GetAttribute<T>() != null;
        }

        public static bool IsStructType(Type type)
        {
            return GetAttribute(type) != null;
        }

        public static bool IsStructType(object type)
        {
            return GetAttribute(type) != null;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/StructAttribute.cs`.

**Classes defined**: StructAttribute



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 40
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `StructAttribute`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

