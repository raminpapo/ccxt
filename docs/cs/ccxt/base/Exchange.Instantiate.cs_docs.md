# Documentation: cs/ccxt/base/Exchange.Instantiate.cs

## File Metadata

- **Path**: `cs/ccxt/base/Exchange.Instantiate.cs`
- **Size**: 1,819 bytes
- **Lines**: 58
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Reflection;

namespace ccxt;

public partial class Exchange
{
    public static Exchange DynamicallyCreateInstance(string className, object args = null, bool isWs = false)
    {
        var assembly = Assembly.GetExecutingAssembly();

        if (isWs)
        {
            className = "ccxt.pro." + className;
        }

        var type = assembly.GetTypes()
            .First(t => t.Name == className || t.FullName == className);


        // tmp check this, can't find constructor
        // if (args != null)
        // {
        args ??= new Dictionary<string, object>();
        // Type type2 = Type.GetType(className);
        ConstructorInfo constructor = type.GetConstructor(new Type[] { typeof(object) });
        object classInstance = constructor.Invoke(new object[] { args });
        return classInstance as Exchange;
        // }
        // return Activator.CreateInstance(type) as Exchange;
    }
    //     return Activator.CreateInstance(type) as Exchange;
    // }

    public static object DynamicallyCallMethod(Exchange instance, string methodName, object[] parameters)
    {
        var method = instance.GetType().GetMethod(methodName);
        var paramsLength = method.GetParameters().Count();
        if (parameters.Count() < paramsLength)
        {
            var appendedMissingArgs = new object[paramsLength];
            for (int i = 0; i < paramsLength; i++)
            {
                if (i < parameters.Count())
                {
                    appendedMissingArgs[i] = parameters[i];
                }
                else
                {
                    appendedMissingArgs[i] = null;
                }
            }
            return method.Invoke(instance, appendedMissingArgs);

        }
        return method.Invoke(instance, parameters);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/base/Exchange.Instantiate.cs`.

**Classes defined**: Exchange



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 41
- Comment lines: 8
- Blank lines: 9

### Main Components

**Classes** (1):
- `Exchange`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

