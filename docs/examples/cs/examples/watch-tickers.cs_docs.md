# Documentation: examples/cs/examples/watch-tickers.cs

## File Metadata

- **Path**: `examples/cs/examples/watch-tickers.cs`
- **Size**: 476 bytes
- **Lines**: 21
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
// AUTO-TRANSPILE //
async public Task watchTickers()
{
    var binance = new ccxt.pro.binance(new Dictionary<string, object>() {});
    var symbols = new List<string>() {"BTC/USDT", "ETH/USDT", "DOGE/USDT"};
    while (true)
    {
        var tickers = await binance.WatchTickers(symbols);
        Console.WriteLine(JsonConvert.SerializeObject(tickers["BTC/USDT"]));
    }
}


}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/watch-tickers.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 17
- Comment lines: 1
- Blank lines: 3

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

