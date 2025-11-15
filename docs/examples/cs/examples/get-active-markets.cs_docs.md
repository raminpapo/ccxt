# Documentation: examples/cs/examples/get-active-markets.cs

## File Metadata

- **Path**: `examples/cs/examples/get-active-markets.cs`
- **Size**: 635 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;

namespace examples;

partial class Examples
{
    async static public Task getActiveMarkets()
    {
        var exchange = new ccxt.bitget(new Dictionary<string, object>()
        {
            // { "apiKey", "MY_API_KEY" },
            // { "secret", "MY_SECRET" },
        });
        var markets = await exchange.LoadMarkets();
        var marketValues = markets.Values.ToList();
        var activeMarkets = marketValues.FindAll(m => m.active != null && m.active.Value);
        var activeSymbols = activeMarkets.Select(m => m.symbol);
        Console.WriteLine(string.Join(",", activeSymbols));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/get-active-markets.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 17
- Comment lines: 2
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

