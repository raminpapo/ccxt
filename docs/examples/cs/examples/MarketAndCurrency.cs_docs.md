# Documentation: examples/cs/examples/MarketAndCurrency.cs

## File Metadata

- **Path**: `examples/cs/examples/MarketAndCurrency.cs`
- **Size**: 768 bytes
- **Lines**: 25
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public async static Task MarketAndCurrency()
    {
        var exchange = new ccxt.okx();
        exchange.apiKey = Environment.GetEnvironmentVariable("OKX_APIKEY");
        exchange.secret = Environment.GetEnvironmentVariable("OKX_SECRET");
        await exchange.LoadMarkets();
        
        // market info
        var symbol = "BTC/USDT:USDT";
        var market = exchange.Market(symbol);
        Console.WriteLine($"Contract size {market.contractSize}");
        
        // currency info
        var currency = exchange.Currency("USDT");
        var networks = currency.networks.Keys;
        Console.WriteLine($"USDT has support for {String.Join(",", networks)}");
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/MarketAndCurrency.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 19
- Comment lines: 2
- Blank lines: 4

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

