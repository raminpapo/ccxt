# Documentation: cs/ccxt/static/Cryptography.ECDSA/Hex.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Hex.cs`
- **Size**: 1,745 bytes
- **Lines**: 60
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Linq;

namespace Cryptography.ECDSA
{
    public static class Hex
    {
        public static int HexToInteger(byte[] hex)
        {
            var result = 0;
            for (var i = 0; i < hex.Length; i++)
                result = (result << 8) | hex[i];
            return result;
        }

        public static byte[] HexToBytes(string hex)
        {
            if (hex.Length % 2 != 0)
                hex = "0" + hex;

            byte[] arr = new byte[hex.Length >> 1];
            for (int i = 0; i < arr.Length; ++i)
                arr[i] = (byte)((GetHexVal(hex[i << 1]) << 4) + (GetHexVal(hex[(i << 1) + 1])));

            return arr;
        }

        private static int GetHexVal(char hex)
        {
            int val = hex;
            //For uppercase A-F letters:
            //return val - (val < 58 ? 48 : 55);
            //For lowercase a-f letters:
            //return val - (val < 58 ? 48 : 87);
            //Or the two combined, but a bit slower:
            return val - (val < 58 ? 48 : (val < 97 ? 55 : 87));
        }

        public static byte[] Join(params byte[][] values)
        {
            var len = values.Sum(i => i.Length);
            var rez = new byte[len];
            var k = 0;
            for (var i = 0; i < values.Length; i++)
            {
                var source = values[i];
                if (source.Length == 0)
                    continue;
                Array.Copy(source, 0, rez, k, source.Length);
                k += source.Length;
            }
            return rez;
        }

        public static string ToString(byte[] hex)
        {
            return string.Join(string.Empty, hex.Select(i => i.ToString("x2")));
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Hex.cs`.

**Classes defined**: Hex



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 48
- Comment lines: 5
- Blank lines: 7

### Main Components

**Classes** (1):
- `Hex`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

