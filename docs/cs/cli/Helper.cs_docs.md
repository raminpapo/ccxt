# Documentation: cs/cli/Helper.cs

## File Metadata

- **Path**: `cs/cli/Helper.cs`
- **Size**: 825 bytes
- **Lines**: 33
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Newtonsoft.Json;

namespace Example;

public class Helper
{
    public static void Green(string message)
    {
        System.Console.ForegroundColor = System.ConsoleColor.Green;
        System.Console.WriteLine(message);
        System.Console.ResetColor();
    }

    public static void Red(string message)
    {
        System.Console.ForegroundColor = System.ConsoleColor.Red;
        System.Console.WriteLine(message);
        System.Console.ResetColor();
    }

    public static void Warn(string message)
    {
        System.Console.ForegroundColor = System.ConsoleColor.Yellow;
        System.Console.WriteLine(message);
        System.Console.ResetColor();
    }

    public static void print(object message)
    {
        Console.WriteLine(JsonConvert.SerializeObject(message, Formatting.Indented));
    }
}

```

## High-Level Overview

This is a C# file located at `cs/cli/Helper.cs`.

**Classes defined**: Helper



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 27
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `Helper`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

