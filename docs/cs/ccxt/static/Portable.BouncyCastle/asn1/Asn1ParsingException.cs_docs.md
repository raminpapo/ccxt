# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1ParsingException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1ParsingException.cs`
- **Size**: 539 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Asn1
{
    [Serializable]
    public class Asn1ParsingException
		: InvalidOperationException
	{
		public Asn1ParsingException()
			: base()
		{
		}

		public Asn1ParsingException(string message)
			: base(message)
		{
		}

		public Asn1ParsingException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected Asn1ParsingException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1ParsingException.cs`.

**Classes defined**: Asn1ParsingException



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 26
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `Asn1ParsingException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

