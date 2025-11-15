# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/MaxBytesExceededException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/MaxBytesExceededException.cs`
- **Size**: 710 bytes
- **Lines**: 34
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Crypto
{
	/// <summary>This exception is thrown whenever a cipher requires a change of key, IV or similar after x amount of
	/// bytes enciphered.
	/// </summary>
    [Serializable]
    public class MaxBytesExceededException
		: CryptoException
	{
		public MaxBytesExceededException()
			: base()
		{
		}

		public MaxBytesExceededException(string message)
			: base(message)
		{
		}

		public MaxBytesExceededException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected MaxBytesExceededException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/MaxBytesExceededException.cs`.

**Classes defined**: MaxBytesExceededException



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 26
- Comment lines: 3
- Blank lines: 5

### Main Components

**Classes** (1):
- `MaxBytesExceededException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

