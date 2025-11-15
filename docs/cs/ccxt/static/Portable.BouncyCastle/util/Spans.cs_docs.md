# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/Spans.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/Spans.cs`
- **Size**: 447 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
using System;
using System.Runtime.CompilerServices;

#nullable enable

namespace Org.BouncyCastle.Utilities
{
    internal static class Spans
    {
        [MethodImpl(MethodImplOptions.AggressiveInlining)]
        internal static Span<T> FromNullable<T>(T[]? array, int start)
        {
            return array == null ? Span<T>.Empty : array.AsSpan(start);
        }
    }
}
#endif

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/Spans.cs`.

**Classes defined**: Spans



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 14
- Comment lines: 2
- Blank lines: 3

### Main Components

**Classes** (1):
- `Spans`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

