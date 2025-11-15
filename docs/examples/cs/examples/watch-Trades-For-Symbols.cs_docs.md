# Documentation: examples/cs/examples/watch-Trades-For-Symbols.cs

## File Metadata

- **Path**: `examples/cs/examples/watch-Trades-For-Symbols.cs`
- **Size**: 508 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    async static public Task watchTradesForSymbols()
    {
        var binance = new ccxt.pro.binance(new Dictionary<string, object>() { });
        var symbols = new List<string>() { "BTC/USDT", "ETH/USDT", "DOGE/USDT" };
        while (true)
        {
            var trades = await binance.WatchTradesForSymbols(symbols);
            Console.WriteLine(JsonConvert.SerializeObject(trades));
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/watch-Trades-For-Symbols.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 17
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

