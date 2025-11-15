# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Exception.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Exception.cs`
- **Size**: 507 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Asn1
{
    [Serializable]
    public class Asn1Exception
		: IOException
	{
		public Asn1Exception()
			: base()
		{
		}

		public Asn1Exception(string message)
			: base(message)
		{
		}

		public Asn1Exception(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected Asn1Exception(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Exception.cs`.

**Classes defined**: Asn1Exception



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 27
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `Asn1Exception`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

