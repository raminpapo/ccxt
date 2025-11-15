# Documentation: examples/cs/examples/watchPositionsForSymbols.cs

## File Metadata

- **Path**: `examples/cs/examples/watchPositionsForSymbols.cs`
- **Size**: 575 bytes
- **Lines**: 22
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;

namespace examples;

partial class Examples
{
    async public Task watchPositionsForSymbols()
    {
        var exchange = new ccxt.pro.binanceusdm(new Dictionary<string, object>()
        {
            { "apiKey", "YOUR_API_KEY" },
            { "secret", "Your_API_SECRET" },
        });
        var symbols = new List<string>() { "BTC/USDT:USDT", "ETH/USDT:USDT", "DOGE/USDT:USDT" };
        while (true)
        {
            var positions = await exchange.WatchPositions(symbols);
            Console.WriteLine(positions);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/watchPositionsForSymbols.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 20
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

