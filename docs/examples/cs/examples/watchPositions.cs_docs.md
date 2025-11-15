# Documentation: examples/cs/examples/watchPositions.cs

## File Metadata

- **Path**: `examples/cs/examples/watchPositions.cs`
- **Size**: 528 bytes
- **Lines**: 22
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    async public Task watchPositions()
    {
        var exchange = new ccxt.pro.binanceusdm(new Dictionary<string, object>()
        {
            { "apiKey", "YOUR_API_KEY" },
            { "secret", "YOUR_API_SECRET" },
        });
        while (true)
        {
            var trades = await exchange.WatchPositions();
            Console.WriteLine(JsonConvert.SerializeObject(trades, Formatting.Indented));
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/watchPositions.cs`.

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

