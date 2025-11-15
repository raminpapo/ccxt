# Documentation: cs/ccxt/static/Portable.BouncyCastle/openssl/EncryptionException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/openssl/EncryptionException.cs`
- **Size**: 541 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Security
{
    [Serializable]
    public class EncryptionException
		: IOException
	{
		public EncryptionException()
			: base()
		{
		}

		public EncryptionException(string message)
			: base(message)
		{
		}

		public EncryptionException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected EncryptionException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/openssl/EncryptionException.cs`.

**Classes defined**: EncryptionException



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 27
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `EncryptionException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

