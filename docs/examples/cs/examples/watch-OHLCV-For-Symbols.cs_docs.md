# Documentation: examples/cs/examples/watch-OHLCV-For-Symbols.cs

## File Metadata

- **Path**: `examples/cs/examples/watch-OHLCV-For-Symbols.cs`
- **Size**: 500 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;
namespace examples;
partial class Examples
{
async public Task watchOHLCVForSymbols()
{
    var binance = new ccxt.pro.binance(new Dictionary<string, object>() {});
    var subscriptions = new List<List<string>>() {new List<string>() {"BTC/USDT", "5m"}, new List<string>() {"ETH/USDT", "5m"}, new List<string>() {"BTC/USDT", "1h"}};
    while (true)
    {
        var ohlcv = await binance.WatchOHLCVForSymbols(subscriptions);
        Console.WriteLine(ohlcv);
    }
}


}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/watch-OHLCV-For-Symbols.cs`.

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

