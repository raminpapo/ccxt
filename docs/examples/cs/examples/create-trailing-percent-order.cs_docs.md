# Documentation: examples/cs/examples/create-trailing-percent-order.cs

## File Metadata

- **Path**: `examples/cs/examples/create-trailing-percent-order.cs`
- **Size**: 1,543 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;

namespace examples;

partial class Examples
{
    async public Task createTrailingPercentOrder()
    {
        var exchange = new ccxt.bingx(new Dictionary<string, object>()
        {
            { "apiKey", "MY_API_KEY" },
            { "secret", "MY_SECRET" },
        });
        // exchange.setSandboxMode (true);
        // exchange.verbose = true; // uncomment for debugging purposes if necessary
        await exchange.LoadMarkets();
        var symbol = "BTC/USDT:USDT";
        var orderType = "market";
        var side = "sell";
        var amount = 0.0001;
        double? price = null;
        var reduceOnly = true;
        var trailingPercent = 10;
        // const trailingTriggerPrice = undefined; // not supported on all exchanges
        var parameters = new Dictionary<string, object>()
        {
            { "reduceOnly", reduceOnly },
            { "trailingPercent", trailingPercent },
        };
        try
        {
            var createOrder = await exchange.CreateOrder(symbol, orderType, side, amount, price, parameters);
            // Alternatively use the createTrailingAmountOrder method:
            // const create_order = await exchange.createTrailingPercentOrder (symbol, order_type, side, amount, price, trailingPercent, trailingTriggerPrice, {
            //     'reduceOnly': reduceOnly,
            // });
            Console.WriteLine(createOrder);
        }
        catch (Exception e)
        {
            Console.WriteLine(((object)e).ToString());
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/create-trailing-percent-order.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 36
- Comment lines: 7
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

