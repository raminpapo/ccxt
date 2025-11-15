# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Util.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Util.cs`
- **Size**: 1,449 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Security;

namespace Cryptography.ECDSA.Internal.Secp256K1
{
    internal class Util
    {
        public static void Memcpy(Array src, UInt32 srcOffset, Array dst, UInt32 dstOffset, UInt32 count)
        {
            if (count > int.MaxValue)
                throw new InvalidCastException(nameof(count));

            if (dstOffset > int.MaxValue)
                throw new InvalidCastException(nameof(dstOffset));

            if (srcOffset > int.MaxValue)
                throw new InvalidCastException(nameof(srcOffset));

            Buffer.BlockCopy(src, (int)srcOffset, dst, (int)dstOffset, (int)count);
        }

        public static void Memcpy(Array src, int srcOffset, Array dst, int dstOffset, int count)
        {
            Buffer.BlockCopy(src, srcOffset, dst, dstOffset, count);
        }

        internal static void MemSet(byte[] dest, byte val, int size)
        {
            for (var i = 0; i < size && i < dest.Length; i++)
                dest[i] = val;
        }

        internal static void MemSet(byte[] dest, UInt32 skip, byte val, UInt32 size)
        {
            for (var i = skip; i < size && i < dest.Length; i++)
                dest[i] = val;
        }

        internal static UInt32 BitToUInt32Invers(byte[] b32, int index)
        {
            return b32[index + 3] | (UInt32)b32[index + 2] << 8 | (UInt32)b32[index + 1] << 16 | (UInt32)b32[index] << 24;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/Util.cs`.

**Classes defined**: Util



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 36
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `Util`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

