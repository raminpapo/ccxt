# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DERSequenceGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DERSequenceGenerator.cs`
- **Size**: 828 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.IO;

namespace Org.BouncyCastle.Asn1
{
	public class DerSequenceGenerator
		: DerGenerator
	{
		private readonly MemoryStream _bOut = new MemoryStream();

		public DerSequenceGenerator(
			Stream outStream)
			: base(outStream)
		{
		}

		public DerSequenceGenerator(
			Stream	outStream,
			int		tagNo,
			bool	isExplicit)
			: base(outStream, tagNo, isExplicit)
		{
		}

		public override void AddObject(Asn1Encodable obj)
		{
            obj.EncodeTo(_bOut, Asn1Encodable.Der);
		}

        public override void AddObject(Asn1Object obj)
        {
            obj.EncodeTo(_bOut, Asn1Encodable.Der);
        }

        public override Stream GetRawOutputStream()
		{
			return _bOut;
		}

		public override void Close()
		{
			WriteDerEncoded(Asn1Tags.Constructed | Asn1Tags.Sequence, _bOut.ToArray());
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DERSequenceGenerator.cs`.

**Classes defined**: DerSequenceGenerator



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 37
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `DerSequenceGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

