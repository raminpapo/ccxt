# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/Times.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/Times.cs`
- **Size**: 278 bytes
- **Lines**: 15
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Utilities
{
    public sealed class Times
    {
        private static long NanosecondsPerTick = 100L;

        public static long NanoTime()
        {
            return DateTime.UtcNow.Ticks * NanosecondsPerTick;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/Times.cs`.

**Classes defined**: Times



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 12
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `Times`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

