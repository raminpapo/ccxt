# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/BERSetGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/BERSetGenerator.cs`
- **Size**: 426 bytes
- **Lines**: 25
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.IO;

namespace Org.BouncyCastle.Asn1
{
	public class BerSetGenerator
		: BerGenerator
	{
		public BerSetGenerator(
			Stream outStream)
			: base(outStream)
		{
			WriteBerHeader(Asn1Tags.Constructed | Asn1Tags.Set);
		}

		public BerSetGenerator(
			Stream	outStream,
			int		tagNo,
			bool	isExplicit)
			: base(outStream, tagNo, isExplicit)
		{
			WriteBerHeader(Asn1Tags.Constructed | Asn1Tags.Set);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/BERSetGenerator.cs`.

**Classes defined**: BerSetGenerator



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 22
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `BerSetGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

