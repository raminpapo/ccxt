# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/io/DigestSink.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/io/DigestSink.cs`
- **Size**: 994 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Crypto.IO
{
    public sealed class DigestSink
        : BaseOutputStream
    {
        private readonly IDigest m_digest;

        public DigestSink(IDigest digest)
        {
            m_digest = digest;
        }

        public IDigest Digest => m_digest;

        public override void Write(byte[] buffer, int offset, int count)
        {
            Streams.ValidateBufferArguments(buffer, offset, count);

            if (count > 0)
            {
                m_digest.BlockUpdate(buffer, offset, count);
            }
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override void Write(ReadOnlySpan<byte> buffer)
        {
            if (!buffer.IsEmpty)
            {
                m_digest.BlockUpdate(buffer);
            }
        }
#endif

        public override void WriteByte(byte value)
        {
            m_digest.Update(value);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/io/DigestSink.cs`.

**Classes defined**: DigestSink



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 34
- Comment lines: 2
- Blank lines: 9

### Main Components

**Classes** (1):
- `DigestSink`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

