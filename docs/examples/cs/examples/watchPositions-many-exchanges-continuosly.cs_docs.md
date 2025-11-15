# Documentation: examples/cs/examples/watchPositions-many-exchanges-continuosly.cs

## File Metadata

- **Path**: `examples/cs/examples/watchPositions-many-exchanges-continuosly.cs`
- **Size**: 2,276 bytes
- **Lines**: 77
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
    async public Task<List<Position>> watchPositionsContinuously(Exchange exchange)
    {
        while (true)
        {
            try
            {
                var positions = await exchange.WatchPositions();
                Console.WriteLine("Fetched " + exchange.id + " - Positions: " + JsonConvert.SerializeObject(positions));
                return positions;
            }
            catch (Exception e)
            {
                Console.WriteLine(e);
                break;
            }
        }

        return null;
    }

    // start exchanges and fetch OHLCV loop
    async public Task initializeExchange(string exchangeName, object config)
    {
        var ex = Exchange.DynamicallyCreateInstance("ccxt.pro." + exchangeName, config);
        var promises = new List<Task<List<Position>>>() { };
        (promises).Add(watchPositionsContinuously(ex));
        await Task.WhenAll(promises);
        await ex.Close();
    }

    // main function
    async public Task watchPositionsManyExchangesContinuosly()
    {
        var exchanges = new Dictionary<string, object>()
        {
            {
                "binanceusdm", new Dictionary<string, object>()
                {
                    { "apiKey", "YOUR_API_KEY" },
                    { "secret", "YOUR_API_SECRET" },
                }
            },
            {
                "okx", new Dictionary<string, object>()
                {
                    { "apiKey", "YOUR_API_KEY" },
                    { "secret", "YOUR_API_SECRET" },
                }
            },
            {
                "huobi", new Dictionary<string, object>()
                {
                    { "apiKey", "YOUR_API_KEY" },
                    { "secret", "YOUR_API_SECRET" },
                }
            },
        };
        var promises = new List<Task>() { };
        var exchangeIds = exchanges.Keys.ToList();
        for (var i = 0; i < exchangeIds.Count; i++)
        {
            var exchangeName = exchangeIds[i];
            var config = exchanges[exchangeName];
            promises.Add(initializeExchange(exchangeName, config));
        }

        await Task.WhenAll(promises);
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/watchPositions-many-exchanges-continuosly.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 77
- Code lines: 69
- Comment lines: 2
- Blank lines: 6

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

