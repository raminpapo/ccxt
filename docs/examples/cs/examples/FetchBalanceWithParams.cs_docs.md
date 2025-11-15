# Documentation: examples/cs/examples/FetchBalanceWithParams.cs

## File Metadata

- **Path**: `examples/cs/examples/FetchBalanceWithParams.cs`
- **Size**: 601 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public async static Task FetchBalance()
    {
        var exchange = new Bybit();
        exchange.apiKey = Environment.GetEnvironmentVariable("BYBIT_APIKEY");
        exchange.secret = Environment.GetEnvironmentVariable("BYBIT_SECRET");
        exchange.setSandboxMode(true);
        var parameters = new Dictionary<string, object>() { { "type", "swap" } };
        var balance = await exchange.FetchBalance(parameters);
        Console.WriteLine(JsonConvert.SerializeObject(balance, Formatting.Indented));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/FetchBalanceWithParams.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 16
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

