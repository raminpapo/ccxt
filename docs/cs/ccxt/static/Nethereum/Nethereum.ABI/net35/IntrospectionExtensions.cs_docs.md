# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/net35/IntrospectionExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/net35/IntrospectionExtensions.cs`
- **Size**: 1,827 bytes
- **Lines**: 59
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿#if DOTNET35
namespace System.Reflection
{

    using System.Collections.Generic;
    public static class IntrospectionExtensions
    {
        // This allows us to use the new reflection API which separates Type and TypeInfo
        // while still supporting .NET 3.5 and 4.0. This class matches the API of the same
        // class in .NET 4.5+, and so is only needed on .NET Framework versions before that.
        //
        public static Type GetTypeInfo(this Type type)
        {
            return type;
        }

        public static T GetCustomAttribute<T>(this Type type)
        {
            return GetCustomAttribute<T>(type, false);
        }

        public static T GetCustomAttribute<T>(this Type type, bool inherited)
        {
            var attributes = type.GetCustomAttributes(typeof(T), inherited);
            if (attributes.Length > 0) return (T)attributes[0];
            return default(T);
        }

        public static T GetCustomAttribute<T>(this PropertyInfo propertyInfo, bool inherited)
        {
            var attributes = propertyInfo.GetCustomAttributes(typeof(T), inherited);
            if (attributes.Length > 0) return (T)attributes[0];
            return default(T);
        }


        public static T GetCustomAttribute<T>(this PropertyInfo propertyInfo)
        {
            return GetCustomAttribute<T>(propertyInfo, false);
        }

        public static IEnumerable<PropertyInfo> DeclaredProperties(this Type type)
        {
              return type.GetProperties();
        }

        public static IEnumerable<Type> ImplementedInterfaces(this Type type)
        {
            return type.GetInterfaces();
        }

        public static Type[] GenericTypeArguments(this Type type)
        {
            return type.GetGenericArguments();
        }
    }

}
#endif
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/net35/IntrospectionExtensions.cs`.

**Classes defined**: IntrospectionExtensions, in, matches



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 44
- Comment lines: 5
- Blank lines: 10

### Main Components

**Classes** (1):
- `IntrospectionExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

