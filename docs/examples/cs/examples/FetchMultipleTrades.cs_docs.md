# Documentation: examples/cs/examples/FetchMultipleTrades.cs

## File Metadata

- **Path**: `examples/cs/examples/FetchMultipleTrades.cs`
- **Size**: 592 bytes
- **Lines**: 22
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public static async Task FetchMultipleTrades()
    {
        var exchange = new Binance();
        var symbols = new string[] { "BTC/USDT", "ETH/USDT", "LTC/USDT", "XRP/USDT" };

        var tasks = new List<Task<List<ccxt.Trade>>>();
        foreach (var value in symbols)
        {
            tasks.Add(exchange.FetchTrades(value, null, 1));
        }

        var result = await Task.WhenAll(tasks.ToArray());
        Console.WriteLine(JsonConvert.SerializeObject(result, Formatting.Indented));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/FetchMultipleTrades.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 18
- Comment lines: 0
- Blank lines: 4

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

