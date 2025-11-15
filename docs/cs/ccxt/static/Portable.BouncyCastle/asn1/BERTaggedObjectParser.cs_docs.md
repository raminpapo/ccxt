# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/BERTaggedObjectParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/BERTaggedObjectParser.cs`
- **Size**: 1,934 bytes
- **Lines**: 81
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Asn1
{
	internal class BerTaggedObjectParser
		: Asn1TaggedObjectParser
	{
        internal readonly int m_tagClass;
        internal readonly int m_tagNo;
        internal readonly Asn1StreamParser m_parser;

		internal BerTaggedObjectParser(int tagClass, int tagNo, Asn1StreamParser parser)
		{
            m_tagClass = tagClass;
            m_tagNo = tagNo;
            m_parser = parser;
		}

		public virtual bool IsConstructed
		{
			get { return true; }
		}

        public int TagClass
        {
            get { return m_tagClass; }
        }

		public int TagNo
		{
			get { return m_tagNo; }
		}

        public bool HasContextTag(int tagNo)
        {
            return m_tagClass == Asn1Tags.ContextSpecific && m_tagNo == tagNo;
        }

        public bool HasTag(int tagClass, int tagNo)
        {
            return m_tagClass == tagClass && m_tagNo == tagNo;
        }

        public virtual IAsn1Convertible ParseBaseUniversal(bool declaredExplicit, int baseTagNo)
        {
            if (declaredExplicit)
                return m_parser.ParseObject(baseTagNo);

            return m_parser.ParseImplicitConstructedIL(baseTagNo);
        }

        public virtual IAsn1Convertible ParseExplicitBaseObject()
        {
            return m_parser.ReadObject();
        }

        public virtual Asn1TaggedObjectParser ParseExplicitBaseTagged()
        {
            return m_parser.ParseTaggedObject();
        }

        public virtual Asn1TaggedObjectParser ParseImplicitBaseTagged(int baseTagClass, int baseTagNo)
        {
            return new BerTaggedObjectParser(baseTagClass, baseTagNo, m_parser);
        }

        public virtual Asn1Object ToAsn1Object()
		{
			try
			{
                return m_parser.LoadTaggedIL(TagClass, TagNo);
            }
			catch (IOException e)
			{
				throw new Asn1ParsingException(e.Message);
			}
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/BERTaggedObjectParser.cs`.

**Classes defined**: BerTaggedObjectParser



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 67
- Comment lines: 0
- Blank lines: 14

### Main Components

**Classes** (1):
- `BerTaggedObjectParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

