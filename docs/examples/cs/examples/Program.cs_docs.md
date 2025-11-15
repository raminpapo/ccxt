# Documentation: examples/cs/examples/Program.cs

## File Metadata

- **Path**: `examples/cs/examples/Program.cs`
- **Size**: 428 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using ccxt;
using Newtonsoft.Json;

namespace examples;

partial class Examples
{
    public static void Main(string[] args)
    {
        // FetchMarkets();
        // FetchTrades();
        // FetchOrderBook();
        // FetchBalance().Wait();
        // FetchPositions().Wait();
        watchTradesForSymbols().Wait();
        // new Examples().UnWatchOrders().Wait();
        // SetMarketsFromExchange().Wait();
    }
}

```

## High-Level Overview

This is a C# file located at `examples/cs/examples/Program.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 10
- Comment lines: 7
- Blank lines: 3

### Main Components

**Classes** (1):
- `Examples`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

