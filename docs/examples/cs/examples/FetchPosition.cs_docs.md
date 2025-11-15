# Documentation: examples/cs/examples/FetchPosition.cs

## File Metadata

- **Path**: `examples/cs/examples/FetchPosition.cs`
- **Size**: 524 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public async static Task FetchPositions()
    {
        var exchange = new Bybit();
        exchange.apiKey = "";
        exchange.secret = "";
        exchange.setSandboxMode(true);
        var symbols = new List<string>() { "LTC/USDT:USDT" };
        var positions = await exchange.FetchPositions(symbols);
        var first = positions[0];
        Console.WriteLine(JsonConvert.SerializeObject(positions, Formatting.Indented));
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/FetchPosition.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 17
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

