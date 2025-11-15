# Documentation: cs/ccxt/static/Portable.BouncyCastle/security/InvalidKeyException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/security/InvalidKeyException.cs`
- **Size**: 525 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Security
{
    [Serializable]
    public class InvalidKeyException
		: KeyException
	{
		public InvalidKeyException()
			: base()
		{
		}

		public InvalidKeyException(string message)
			: base(message)
		{
		}

		public InvalidKeyException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected InvalidKeyException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/security/InvalidKeyException.cs`.

**Classes defined**: InvalidKeyException



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 26
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `InvalidKeyException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

