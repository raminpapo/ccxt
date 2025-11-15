# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/DataLengthException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/DataLengthException.cs`
- **Size**: 836 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Crypto
{
	/// <summary>This exception is thrown if a buffer that is meant to have output copied into it turns out to be too
	/// short, or if we've been given insufficient input.</summary>
	/// <remarks>
	/// In general this exception will get thrown rather than an <see cref="IndexOutOfRangeException"/>.
	/// </remarks>
	[Serializable]
    public class DataLengthException
		: CryptoException
	{
		public DataLengthException()
			: base()
		{
		}

		public DataLengthException(string message)
			: base(message)
		{
		}

		public DataLengthException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected DataLengthException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/DataLengthException.cs`.

**Classes defined**: DataLengthException



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 26
- Comment lines: 5
- Blank lines: 5

### Main Components

**Classes** (1):
- `DataLengthException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

