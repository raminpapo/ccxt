# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/InvalidCipherTextException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/InvalidCipherTextException.cs`
- **Size**: 671 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Crypto
{
	 /// <summary>This exception is thrown whenever we find something we don't expect in a message.</summary>
    [Serializable]
    public class InvalidCipherTextException
		: CryptoException
    {
		public InvalidCipherTextException()
			: base()
		{
		}

		public InvalidCipherTextException(string message)
			: base(message)
		{
		}

		public InvalidCipherTextException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected InvalidCipherTextException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/InvalidCipherTextException.cs`.

**Classes defined**: InvalidCipherTextException



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 26
- Comment lines: 1
- Blank lines: 5

### Main Components

**Classes** (1):
- `InvalidCipherTextException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

