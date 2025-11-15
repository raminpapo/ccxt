# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/Check.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/Check.cs`
- **Size**: 1,113 bytes
- **Lines**: 40
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto
{
    internal class Check
    {
        internal static void DataLength(bool condition, string msg)
        {
            if (condition)
                throw new DataLengthException(msg);
        }

        internal static void DataLength(byte[] buf, int off, int len, string msg)
        {
            if (off > (buf.Length - len))
                throw new DataLengthException(msg);
        }

        internal static void OutputLength(byte[] buf, int off, int len, string msg)
        {
            if (off > (buf.Length - len))
                throw new OutputLengthException(msg);
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        internal static void DataLength(ReadOnlySpan<byte> input, int len, string msg)
        {
            if (input.Length < len)
                throw new DataLengthException(msg);
        }

        internal static void OutputLength(Span<byte> output, int len, string msg)
        {
            if (output.Length < len)
                throw new OutputLengthException(msg);
        }
#endif
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/Check.cs`.

**Classes defined**: Check



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 32
- Comment lines: 2
- Blank lines: 6

### Main Components

**Classes** (1):
- `Check`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

