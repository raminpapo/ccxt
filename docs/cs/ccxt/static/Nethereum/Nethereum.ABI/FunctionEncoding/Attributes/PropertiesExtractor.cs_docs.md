# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/PropertiesExtractor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/PropertiesExtractor.cs`
- **Size**: 1,704 bytes
- **Lines**: 42
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.Linq;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    public static class PropertiesExtractor
    {
        public static IEnumerable<PropertyInfo> GetProperties(Type type)
        {
#if DOTNET35
            var hidingProperties = type.GetProperties().Where(x => PropertyInfoExtensions.IsHidingMember(x));
            var nonHidingProperties = type.GetProperties().Where(x => hidingProperties.All(y => y.Name != x.Name));
            return nonHidingProperties.Concat(hidingProperties);
#else
            var hidingProperties = type.GetRuntimeProperties().Where(x => x.IsHidingMember());
            var nonHidingProperties = type.GetRuntimeProperties().Where(x => hidingProperties.All(y => y.Name != x.Name));
            return nonHidingProperties.Concat(hidingProperties);
#endif
        }

        public static IEnumerable<PropertyInfo> GetPropertiesWithParameterAttribute(Type type)
        {
            return GetProperties(type).Where(x => x.IsDefined(typeof(ParameterAttribute), true));
        }

        public static ParameterAttributeIndexedTopics[] GetIndexedTopics<T>()
        {
            return PropertiesExtractor
                .GetPropertiesWithParameterAttribute(typeof(T))
                .Select(p => new ParameterAttributeIndexedTopics
                {
                    ParameterAttribute = p.GetCustomAttribute<ParameterAttribute>(),
                    PropertyInfo = p
                })
                .Where(p => p.ParameterAttribute?.Parameter.Indexed ?? false)
                .OrderBy(p => p.ParameterAttribute.Order)
                .ToArray();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/PropertiesExtractor.cs`.

**Classes defined**: PropertiesExtractor



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 36
- Comment lines: 3
- Blank lines: 3

### Main Components

**Classes** (1):
- `PropertiesExtractor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

