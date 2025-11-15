# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/BigDecimal.Formatter.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/BigDecimal.Formatter.cs`
- **Size**: 1,323 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text;

namespace Nethereum.Util {
    internal static class BigDecimalFormatter {
        public static string ToCurrencyString(this BigDecimal value, int maxDigits, NumberFormatInfo format) {
            value.Normalize();

            if (maxDigits < 0)
                maxDigits = format.CurrencyDecimalDigits;

            BigDecimal rounded = value.RoundAwayFromZero(significantDigits: maxDigits);
            var digits = rounded.GetDigits(out int exponent);
            var result = new StringBuilder();
            NumberFormatting.FormatCurrency(result,
                rounded.Mantissa < 0, digits, exponent,
                maxDigits: maxDigits, info: format);
            return result.ToString();
        }

        internal static IList<byte> GetDigits(this BigDecimal value, out int exponent) {
            var nonNegativeMantissa = value.Mantissa < 0 ? -value.Mantissa : value.Mantissa;
            var result = new List<byte>();
            while (nonNegativeMantissa > 0) {
                result.Add((byte)(nonNegativeMantissa % 10 + '0'));
                nonNegativeMantissa /= 10;
            }
            result.Reverse();
            exponent = value.Exponent;
            return result;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/BigDecimal.Formatter.cs`.

**Classes defined**: BigDecimalFormatter



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 31
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `BigDecimalFormatter`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

