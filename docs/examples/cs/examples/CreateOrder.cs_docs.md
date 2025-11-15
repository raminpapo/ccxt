# Documentation: examples/cs/examples/CreateOrder.cs

## File Metadata

- **Path**: `examples/cs/examples/CreateOrder.cs`
- **Size**: 839 bytes
- **Lines**: 23
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public async static Task CreateOrder()
    {
        var exchange = new Bybit();
        exchange.apiKey = Environment.GetEnvironmentVariable("BYBIT_APIKEY");
        exchange.secret = Environment.GetEnvironmentVariable("BYBIT_SECRET");
        exchange.setSandboxMode(true);
        var parameters = new Dictionary<string, object>() { { "stopPrice", 120 } };
        var order = await exchange.CreateOrder("LTC/USDT", "limit", "buy", 1, 50, parameters);
        var orderId = order.id;
        Console.WriteLine("Placed Order: Order Id: " + orderId);

        // fetch Order
        var orders = await exchange.FetchOpenOrders("LTC/USDT");
        Console.WriteLine("Fetched Order: " + JsonConvert.SerializeObject(orders, Formatting.Indented));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/CreateOrder.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 19
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

