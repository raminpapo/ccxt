# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DERExternalParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DERExternalParser.cs`
- **Size**: 548 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1
{
	public class DerExternalParser
		: Asn1Encodable
	{
		private readonly Asn1StreamParser m_parser;

		internal DerExternalParser(Asn1StreamParser parser)
		{
			m_parser = parser;
		}

		public IAsn1Convertible ReadObject()
		{
			return m_parser.ReadObject();
		}

		public override Asn1Object ToAsn1Object()
		{
            return Parse(m_parser);
		}

        internal static DerExternal Parse(Asn1StreamParser sp)
        {
            return new DerExternal(sp.ReadVector());
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DERExternalParser.cs`.

**Classes defined**: DerExternalParser



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 25
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `DerExternalParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

