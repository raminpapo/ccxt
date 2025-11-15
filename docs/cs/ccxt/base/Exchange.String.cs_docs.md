# Documentation: cs/ccxt/base/Exchange.String.cs

## File Metadata

- **Path**: `cs/ccxt/base/Exchange.String.cs`
- **Size**: 706 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace ccxt;

public partial class Exchange
{


    public static string BaseUID()
    {
        return Guid.NewGuid().ToString().Replace("-", "");
    }

    public string uuid2()
    {
        return Guid.NewGuid().ToString();
    }

    public string uuid()
    {
        return uuid2();
    }

    public string uuid16()
    {
        return BaseUID().Substring(0, 16);
    }

    public string uuid22()
    {
        return BaseUID().Substring(0, 22);
    }

    public object strip(object str)
    {
        return ((string)str).Trim(); //stub
    }

    public string capitalize(object str2)
    {
        var str = (string)str2;
        return char.ToUpper(str[0]) + str.Substring(1);
    }


}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/base/Exchange.String.cs`.

**Classes defined**: Exchange



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 33
- Comment lines: 0
- Blank lines: 12

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

