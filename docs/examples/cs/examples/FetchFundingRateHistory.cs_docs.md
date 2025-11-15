# Documentation: examples/cs/examples/FetchFundingRateHistory.cs

## File Metadata

- **Path**: `examples/cs/examples/FetchFundingRateHistory.cs`
- **Size**: 341 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public static async Task FetchFundingRateHistory()
    {
        var exchange = new Bybit();
        var fr = await exchange.FetchFundingRateHistory("BTC/USDT:USDT");
        Console.WriteLine(JsonConvert.SerializeObject(fr, Formatting.Indented));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/FetchFundingRateHistory.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 12
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

