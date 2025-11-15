# Documentation: examples/cs/examples/CreateExchangesDynamically.cs

## File Metadata

- **Path**: `examples/cs/examples/CreateExchangesDynamically.cs`
- **Size**: 469 bytes
- **Lines**: 16
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public async static Task CreateExchangesDynamically()
    {
        var exchangeId = "binance";
        var restInstance = Exchange.DynamicallyCreateInstance(exchangeId);
        Console.WriteLine($"Exchange id: {restInstance.id}");
        var wsInstance = Exchange.DynamicallyCreateInstance("binance", null, true);
        Console.WriteLine($"Exchange id {wsInstance.id}");
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/CreateExchangesDynamically.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 14
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `Examples`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

