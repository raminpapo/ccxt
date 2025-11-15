# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/abi.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/abi.cs`
- **Size**: 507 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using StarkSharp.Base.Cairo;
using System;
using System.Collections.Generic;
using System.Linq;

namespace StarknetSharp.Abi
{
    public class Abi
    {
        public Abi(Function[] functions, Event[] events, Struct[] structures)
        {
            Functions = functions;
            Events = events;
            Structures = structures;
        }

        public Function[] Functions { get; set; }
        public Event[] Events { get; set; }
        public Struct[] Structures { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/abi.cs`.

**Classes defined**: Abi



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 19
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `Abi`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

