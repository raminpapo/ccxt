# Documentation: examples/cs/examples/unWatchOrders.cs

## File Metadata

- **Path**: `examples/cs/examples/unWatchOrders.cs`
- **Size**: 2,748 bytes
- **Lines**: 76
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;
using Newtonsoft.Json;
using System;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace examples;
partial class Examples
{
    // Demonstrates the workflow: watchOrders loop, createOrder, unWatchOrders, restart watchOrders, createOrder, then finish
    async public Task UnWatchOrders()
    {
        var bybit = new ccxt.pro.bybit(new Dictionary<string, object>() {
            { "apiKey", "" },
            { "secret", "" },
        });
        bybit.setSandboxMode(true);
        bybit.verbose = true;
        await bybit.LoadMarkets();
        var symbol = "ETC/USDT";

        // Helper function to run watchOrders in a Task
        async Task WatchOrdersLoop()
        {
            try
            {
                while (true)
                {
                    var orders = await bybit.watchOrders(symbol);
                    Console.WriteLine($"[watchOrders] {JsonConvert.SerializeObject(orders)}");
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine($"[watchOrders] Task finished with error: {ex.Message}");
            }
        }

        // 1. Start watchOrders loop in a Task
        var watchTask = Task.Run(WatchOrdersLoop);
        // Wait a bit to let the websocket connect (optional, adjust as needed)
        await Task.Delay(3000);

        // 2. After the Task finishes (simulate by cancelling or error), create an order
        // For demo, we'll cancel the Task after a short delay
        await Task.Delay(5000); // Let it run for 5 seconds
        // In real usage, the Task would finish on error; here we just continue

        // 3. Create an order
        Console.WriteLine("Creating first order...");
        var order1 = await bybit.createOrder(symbol, "market", "buy", 1);
        await Task.Delay(2000);
        Console.WriteLine($"[createOrder] {JsonConvert.SerializeObject(order1)}");

        // 4. Unwatch orders
        Console.WriteLine("Unwatching orders...");
        await bybit.unWatchOrders();

        // 5. Start watchOrders loop again in a new Task
        Console.WriteLine("Starting watchOrders loop again...");
        var watchTask2 = Task.Run(WatchOrdersLoop);
        await Task.Delay(3000);

        // 6. Create another order
        Console.WriteLine("Creating second order...");
        var order2 = await bybit.createOrder(symbol, "market", "buy", 1);
        Console.WriteLine($"[createOrder] {JsonConvert.SerializeObject(order2)}");

        // Optionally, let the second watch run for a bit, then finish
        await Task.Delay(5000);
        // In a real app, you would handle Task cancellation/cleanup here
        Console.WriteLine("Workflow finished.");
    }
}

```

## High-Level Overview

This is a C# file located at `examples/cs/examples/unWatchOrders.cs`.

**Classes defined**: Examples

**Functions defined**: to



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 53
- Comment lines: 13
- Blank lines: 10

### Main Components

**Classes** (1):
- `Examples`

**Functions** (1):
- `to()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

