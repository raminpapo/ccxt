# Documentation: examples/cs/examples/fetch-ohlcv-many-exchanges-continuosly.cs

## File Metadata

- **Path**: `examples/cs/examples/fetch-ohlcv-many-exchanges-continuosly.cs`
- **Size**: 1,556 bytes
- **Lines**: 55
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
    async public Task fetchOHLCVContinuously(Exchange exchange, string symbol)
    {
        while (true)
        {
            try
            {
                var ohlcv = await exchange.FetchOHLCV(symbol);
                var ohlcvLength = ohlcv.Count;
                Console.WriteLine(JsonConvert.SerializeObject(ohlcv));
            }
            catch (Exception e)
            {
                Console.WriteLine(e);
                break;
            }
        }
    }

    // start exchanges and fetch OHLCV loop
    async public Task startExchange(string exchangeName, List<string> symbols)
    {
        var ex = Exchange.DynamicallyCreateInstance(exchangeName);
        var promises = new List<Task>() { };
        for (var i = 0; i < symbols.Count; i++)
        {
            var symbol = symbols[i];
            promises.Add(fetchOHLCVContinuously(ex, symbol));
        }

        await Task.WhenAll(promises);
        await ex.close();
    }

    // main function
    async public Task fetchOhlcvManyExchangesContinuosly()
    {
        var exchanges = new List<string>() { "binance", "okx", "kraken" };
        var symbols = new List<string>() { "BTC/USDT", "ETH/USDT" };
        var promises = new List<Task>() { };
        for (var i = 0; i < exchanges.Count; i++)
        {
            var exchangeName = exchanges[i];
            promises.Add(startExchange(exchangeName, symbols));
        }
        await Task.WhenAll(promises);
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/fetch-ohlcv-many-exchanges-continuosly.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 48
- Comment lines: 2
- Blank lines: 5

### Main Components

**Classes** (1):
- `Examples`

**Functions** (1):
- `async()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

