# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterAttributeIndexedTopics.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterAttributeIndexedTopics.cs`
- **Size**: 622 bytes
- **Lines**: 22
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Collections.Generic;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    public class ParameterAttributeIndexedTopics
    {
        public ParameterAttributeIndexedTopics()
        {
            Topics = new List<object>();
        }
        public ParameterAttribute ParameterAttribute { get; set; }
        public List<object> Topics { get; set; }
        public PropertyInfo PropertyInfo { get; set; }

        public object[] GetTopicValues()
        {
            if (Topics == null || Topics.Count == 0) return null;
            return Topics.ToArray();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/ParameterAttributeIndexedTopics.cs`.

**Classes defined**: ParameterAttributeIndexedTopics



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 20
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `ParameterAttributeIndexedTopics`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

