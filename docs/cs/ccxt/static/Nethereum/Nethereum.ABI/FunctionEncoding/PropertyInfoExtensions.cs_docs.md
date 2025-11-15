# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/PropertyInfoExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/PropertyInfoExtensions.cs`
- **Size**: 1,839 bytes
- **Lines**: 64
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Reflection;

namespace Nethereum.ABI.FunctionEncoding
{
    public static class PropertyInfoExtensions
    {
#if DOTNET35
        public static bool IsHidingMember(this PropertyInfo self)
        {
            Type baseType = self.DeclaringType.GetTypeInfo().BaseType;
            PropertyInfo baseProperty = baseType.GetProperty(self.Name);

            if (baseProperty == null)
            {
                return false;
            }

            if (baseProperty.DeclaringType == self.DeclaringType)
            {
                return false;
            }

            var baseMethodDefinition = baseProperty.GetGetMethod().GetBaseDefinition();
            var thisMethodDefinition = self.GetGetMethod().GetBaseDefinition();


            return baseMethodDefinition.DeclaringType != thisMethodDefinition.DeclaringType;
        }
#else
        public static bool IsHidingMember(this PropertyInfo self)
        {
            try
            {
                Type baseType = self.DeclaringType.GetTypeInfo().BaseType;
                PropertyInfo baseProperty = baseType.GetRuntimeProperty(self.Name);

                if (baseProperty == null)
                {
                    return false;
                }

                if (baseProperty.DeclaringType == self.DeclaringType)
                {
                    return false;
                }

                var baseMethodDefinition = baseProperty.GetMethod.GetRuntimeBaseDefinition();
                var thisMethodDefinition = self.GetMethod.GetRuntimeBaseDefinition();

                return baseMethodDefinition.DeclaringType != thisMethodDefinition.DeclaringType;
            }
            catch (System.Reflection.AmbiguousMatchException)
            {
                return true;
            }
  

        }
#endif
    }
 }

   
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/PropertyInfoExtensions.cs`.

**Classes defined**: PropertyInfoExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 47
- Comment lines: 3
- Blank lines: 14

### Main Components

**Classes** (1):
- `PropertyInfoExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

