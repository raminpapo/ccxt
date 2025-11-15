# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/raw/Bits.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/raw/Bits.cs`
- **Size**: 737 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.Raw
{
    internal abstract class Bits
    {
        internal static uint BitPermuteStep(uint x, uint m, int s)
        {
            uint t = (x ^ (x >> s)) & m;
            return (t ^ (t << s)) ^ x;
        }

        internal static ulong BitPermuteStep(ulong x, ulong m, int s)
        {
            ulong t = (x ^ (x >> s)) & m;
            return (t ^ (t << s)) ^ x;
        }

        internal static uint BitPermuteStepSimple(uint x, uint m, int s)
        {
            return ((x & m) << s) | ((x >> s) & m);
        }

        internal static ulong BitPermuteStepSimple(ulong x, ulong m, int s)
        {
            return ((x & m) << s) | ((x >> s) & m);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/raw/Bits.cs`.

**Classes defined**: Bits



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 25
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `Bits`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

