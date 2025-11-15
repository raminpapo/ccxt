# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DEROctetStringParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DEROctetStringParser.cs`
- **Size**: 640 bytes
- **Lines**: 37
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Asn1
{
	public class DerOctetStringParser
		: Asn1OctetStringParser
	{
		private readonly DefiniteLengthInputStream stream;

		internal DerOctetStringParser(
			DefiniteLengthInputStream stream)
		{
			this.stream = stream;
		}

		public Stream GetOctetStream()
		{
			return stream;
		}

		public Asn1Object ToAsn1Object()
		{
			try
			{
				return new DerOctetString(stream.ToArray());
			}
			catch (IOException e)
			{
				throw new InvalidOperationException("IOException converting stream to byte array: " + e.Message, e);
			}
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DEROctetStringParser.cs`.

**Classes defined**: DerOctetStringParser



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 31
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `DerOctetStringParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

