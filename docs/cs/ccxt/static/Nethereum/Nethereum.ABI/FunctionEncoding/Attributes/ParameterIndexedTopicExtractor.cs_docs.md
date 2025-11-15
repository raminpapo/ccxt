# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterIndexedTopicExtractor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterIndexedTopicExtractor.cs`
- **Size**: 1,109 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.Reflection;
using Nethereum.ABI.FunctionEncoding.AttributeEncoding;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    public static class ParameterIndexedTopicExtractor
    {
        public static List<ParameterAttributeIndexedTopics> GetParameterIndexedTopics(Type type, object instanceValue)
        {
            var properties = PropertiesExtractor.GetPropertiesWithParameterAttribute(type);
            var parameterObjects = new List<ParameterAttributeIndexedTopics>();

            foreach (var property in properties)
            {
                var parameterAttribute = property.GetCustomAttribute<ParameterAttribute>(true);

                if (parameterAttribute.Parameter.Indexed)
                {
                    parameterObjects.Add(new ParameterAttributeIndexedTopics
                    {
                        ParameterAttribute  = parameterAttribute,
                        PropertyInfo = property
                    });
                }
            }
            return parameterObjects;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterIndexedTopicExtractor.cs`.

**Classes defined**: ParameterIndexedTopicExtractor



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 28
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `ParameterIndexedTopicExtractor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

