# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/FunctionAttribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/FunctionAttribute.cs`
- **Size**: 1,636 bytes
- **Lines**: 65
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{

    [AttributeUsage(AttributeTargets.Class)]
    public class FunctionAttribute : Attribute
    {
        public string Name { get; private set; }

        public Type DTOReturnType { get; private set; }

        public string ReturnType { get; private set; }

        public FunctionAttribute(string name, string returnType)
        {
            this.Name = name;
            this.ReturnType = returnType;
        }

        public FunctionAttribute(string name)
        {
            this.Name = name;
        }

        public FunctionAttribute(string name, Type dtoReturnType)
        {
            this.DTOReturnType = dtoReturnType;
            this.Name = name;
        }

        public static FunctionAttribute GetAttribute<T>()
        {
            var type = typeof(T);
            return GetAttribute(type);
        }

        public static FunctionAttribute GetAttribute(Type type)
        {
            return type.GetTypeInfo().GetCustomAttribute<FunctionAttribute>(true);
        }

        public static FunctionAttribute GetAttribute(object instance)
        {
            var type = instance.GetType();
            return GetAttribute(type);
        }

        public static bool IsFunctionType<T>()
        {
            return GetAttribute<T>() != null;
        }

        public static bool IsFunctionType(Type type)
        {
            return GetAttribute(type) != null;
        }

        public static bool IsFunctionType(object type)
        {
            return GetAttribute(type) != null;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/FunctionAttribute.cs`.

**Classes defined**: FunctionAttribute



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 52
- Comment lines: 0
- Blank lines: 13

### Main Components

**Classes** (1):
- `FunctionAttribute`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

