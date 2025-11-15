# Documentation: examples/cs/examples/fetch-ohlcv.cs

## File Metadata

- **Path**: `examples/cs/examples/fetch-ohlcv.cs`
- **Size**: 820 bytes
- **Lines**: 28
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;

namespace examples;

partial class Examples
{
    async public Task fetchOhlcv()
    {
        var myex = new ccxt.okx(new Dictionary<string, object>() { });
        var fromTimestamp = myex.milliseconds() - (86400 * 1000); // last 24 hrs
        var ohlcv = await myex.FetchOHLCV("BTC/USDT", "1m", fromTimestamp, 3, new Dictionary<string, object>()
        {
            { "whatever", 123 },
        });
        var length = ohlcv.Count;
        if (length > 0)
        {
            var lastCandle = ohlcv[length - 1];
            var lastPrice = lastCandle.close;
            Console.WriteLine("Fetched " + length + " candles for " + myex.id + ":  last close " + lastPrice);
        }
        else
        {
            Console.WriteLine("No candles have been fetched");
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/fetch-ohlcv.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 26
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

