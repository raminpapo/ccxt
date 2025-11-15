# Documentation: examples/cs/examples/create-order-ws-example.cs

## File Metadata

- **Path**: `examples/cs/examples/create-order-ws-example.cs`
- **Size**: 912 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;
namespace examples;
partial class Examples
{

    async public Task createOrderWsExample()
    {
        var exchange = new ccxt.pro.binance(new Dictionary<string, object>() {
            { "apiKey", "MY_API_KEY" },
            { "secret", "MY_SECRET" },
        });
        exchange.setSandboxMode(true);
        exchange.verbose = true; // uncomment for debugging purposes if necessary
                                 // load markets
        await exchange.LoadMarkets();
        var symbol = "ETH/USDT";
        var type = "limit";
        var side = "buy";
        var amount = 0.01;
        var price = 1000;
        var orders = new List<ccxt.Order>() { };
        for (var i = 1; i < 5; i++)
        {
            var response = await exchange.CreateOrderWs(symbol, type, side, amount, price);
            price = price + 1;
            orders.Add(response);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/create-order-ws-example.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 28
- Comment lines: 1
- Blank lines: 1

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

