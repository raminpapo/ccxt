# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/EventAttribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/EventAttribute.cs`
- **Size**: 1,356 bytes
- **Lines**: 54
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding.Attributes
{
    [AttributeUsage(AttributeTargets.Class)]
    public class EventAttribute : Attribute
    {
        public EventAttribute(string name) : this(name, false)
        {
        }

        public EventAttribute(string name, bool isAnonymous)
        {
            this.Name = name;
            this.IsAnonymous = isAnonymous;
        }

        public string Name { get; set; }
        public bool IsAnonymous { get; set; }

        public static EventAttribute GetAttribute<T>()
        {
            var type = typeof(T);
            return GetAttribute(type);
        }

        public static EventAttribute GetAttribute(Type type)
        {
            return type.GetTypeInfo().GetCustomAttribute<EventAttribute>(true);
        }

        public static EventAttribute GetAttribute(object instance)
        {
            var type = instance.GetType();
            return GetAttribute(type);
        }

        public static bool IsEventType<T>()
        {
            return GetAttribute<T>() != null;
        }

        public static bool IsEventType(Type type)
        {
            return GetAttribute(type) != null;
        }

        public static bool IsEventType(object type)
        {
            return GetAttribute(type) != null;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/Attributes/EventAttribute.cs`.

**Classes defined**: EventAttribute



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 45
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `EventAttribute`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

