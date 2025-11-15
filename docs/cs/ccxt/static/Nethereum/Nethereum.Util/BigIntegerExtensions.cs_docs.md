# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/BigIntegerExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/BigIntegerExtensions.cs`
- **Size**: 534 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Globalization;
using System.Numerics;

namespace Nethereum.Util
{
    public static class BigIntegerExtensions
    {
        public static int NumberOfDigits(this BigInteger value)
        {
            return (value * value.Sign).ToString().Length;
        }

        public static BigInteger ParseInvariant(string value)
        {
            if (value == null) throw new ArgumentNullException(nameof(value));

            return BigInteger.Parse(value, CultureInfo.InvariantCulture);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/BigIntegerExtensions.cs`.

**Classes defined**: BigIntegerExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 18
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `BigIntegerExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

