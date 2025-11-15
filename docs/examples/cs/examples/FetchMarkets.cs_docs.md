# Documentation: examples/cs/examples/FetchMarkets.cs

## File Metadata

- **Path**: `examples/cs/examples/FetchMarkets.cs`
- **Size**: 335 bytes
- **Lines**: 15
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public static void FetchMarkets()
    {
        var exchange = new Binance();
        var markets = exchange.FetchMarkets();
        markets.Wait();
        Console.WriteLine(JsonConvert.SerializeObject(markets.Result, Formatting.Indented));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/FetchMarkets.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 13
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `Examples`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

