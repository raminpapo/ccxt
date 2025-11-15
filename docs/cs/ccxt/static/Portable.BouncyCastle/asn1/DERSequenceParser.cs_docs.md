# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DERSequenceParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DERSequenceParser.cs`
- **Size**: 508 bytes
- **Lines**: 27
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1
{
    // TODO[asn1] Should be renamed/replaced with DLSequenceParser
    public class DerSequenceParser
		: Asn1SequenceParser
	{
		private readonly Asn1StreamParser m_parser;

		internal DerSequenceParser(Asn1StreamParser parser)
		{
			this.m_parser = parser;
		}

		public IAsn1Convertible ReadObject()
		{
			return m_parser.ReadObject();
		}

		public Asn1Object ToAsn1Object()
		{
            return DLSequence.FromVector(m_parser.ReadVector());
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DERSequenceParser.cs`.

**Classes defined**: DerSequenceParser



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 21
- Comment lines: 1
- Blank lines: 5

### Main Components

**Classes** (1):
- `DerSequenceParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

