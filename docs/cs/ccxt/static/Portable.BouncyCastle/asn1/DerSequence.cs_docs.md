# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DerSequence.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DerSequence.cs`
- **Size**: 2,361 bytes
- **Lines**: 91
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1
{
	public class DerSequence
		: Asn1Sequence
	{
		public static readonly DerSequence Empty = new DerSequence();

		public static DerSequence FromVector(Asn1EncodableVector elementVector)
		{
            return elementVector.Count < 1 ? Empty : new DerSequence(elementVector);
		}

        /**
		 * create an empty sequence
		 */
        public DerSequence()
			: base()
		{
		}

		/**
		 * create a sequence containing one object
		 */
		public DerSequence(Asn1Encodable element)
			: base(element)
		{
		}

        /**
		 * create a sequence containing two objects
		 */
        public DerSequence(Asn1Encodable element1, Asn1Encodable element2)
            : base(element1, element2)
        {
        }

        public DerSequence(params Asn1Encodable[] elements)
            : base(elements)
		{
		}

		/**
		 * create a sequence containing a vector of objects.
		 */
		public DerSequence(Asn1EncodableVector elementVector)
            : base(elementVector)
		{
		}

        internal DerSequence(Asn1Encodable[] elements, bool clone)
            : base(elements, clone)
        {
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            return new ConstructedDLEncoding(Asn1Tags.Universal, Asn1Tags.Sequence,
                Asn1OutputStream.GetContentsEncodings(Asn1OutputStream.EncodingDer, elements));
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            return new ConstructedDLEncoding(tagClass, tagNo,
                Asn1OutputStream.GetContentsEncodings(Asn1OutputStream.EncodingDer, elements));
        }

        internal override DerBitString ToAsn1BitString()
        {
            return new DerBitString(BerBitString.FlattenBitStrings(GetConstructedBitStrings()), false);
        }

        internal override DerExternal ToAsn1External()
        {
            return new DerExternal(this);
        }

        internal override Asn1OctetString ToAsn1OctetString()
        {
            return new DerOctetString(BerOctetString.FlattenOctetStrings(GetConstructedOctetStrings()));
        }

        internal override Asn1Set ToAsn1Set()
        {
            // NOTE: DLSet is intentional, we don't want sorting
            return new DLSet(false, elements);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DerSequence.cs`.

**Classes defined**: DerSequence

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 91
- Code lines: 75
- Comment lines: 13
- Blank lines: 3

### Main Components

**Classes** (1):
- `DerSequence`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

