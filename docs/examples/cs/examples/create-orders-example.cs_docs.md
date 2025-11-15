# Documentation: examples/cs/examples/create-orders-example.cs

## File Metadata

- **Path**: `examples/cs/examples/create-orders-example.cs`
- **Size**: 1,123 bytes
- **Lines**: 39
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;

namespace examples;

partial class Examples
{
// AUTO-TRANSPILE //    
    async public Task createOrdersExample()
    {
        var exchange = new ccxt.binance(new Dictionary<string, object>()
        {
            { "apiKey", "MY_API_KEY" },
            { "secret", "MY_SECRET" },
        });
        exchange.setSandboxMode(true);
        await exchange.LoadMarkets();
        exchange.verbose = true; // uncomment for debugging purposes if necessary
        var orders = await exchange.createOrders(new List<Dictionary<string, object>>()
        {
            new Dictionary<string, object>()
            {
                { "symbol", "LTC/USDT:USDT" },
                { "type", "limit" },
                { "side", "buy" },
                { "amount", 10 },
                { "price", 55 },
            },
            new Dictionary<string, object>()
            {
                { "symbol", "ETH/USDT:USDT" },
                { "type", "market" },
                { "side", "buy" },
                { "amount", 0.5 },
            }
        });
        Console.WriteLine(orders);
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/create-orders-example.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 36
- Comment lines: 1
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

