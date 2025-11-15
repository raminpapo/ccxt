# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/io/SignerSink.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/io/SignerSink.cs`
- **Size**: 808 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Crypto.IO
{
    public sealed class SignerSink
		: BaseOutputStream
	{
		private readonly ISigner m_signer;

        public SignerSink(ISigner signer)
		{
            m_signer = signer;
		}

		public ISigner Signer => m_signer;

		public override void Write(byte[] buffer, int offset, int count)
		{
			Streams.ValidateBufferArguments(buffer, offset, count);

			if (count > 0)
			{
				m_signer.BlockUpdate(buffer, offset, count);
			}
		}

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
		public override void Write(ReadOnlySpan<byte> buffer)
		{
			if (!buffer.IsEmpty)
			{
				m_signer.BlockUpdate(buffer);
			}
		}
#endif

		public override void WriteByte(byte value)
		{
			m_signer.Update(value);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/io/SignerSink.cs`.

**Classes defined**: SignerSink



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 34
- Comment lines: 2
- Blank lines: 9

### Main Components

**Classes** (1):
- `SignerSink`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

