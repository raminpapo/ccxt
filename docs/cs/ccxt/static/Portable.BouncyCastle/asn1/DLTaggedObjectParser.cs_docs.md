# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DLTaggedObjectParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DLTaggedObjectParser.cs`
- **Size**: 2,115 bytes
- **Lines**: 75
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.IO;

namespace Org.BouncyCastle.Asn1
{
    /**
     * Parser for definite-length tagged objects.
     */
    internal class DLTaggedObjectParser
        : BerTaggedObjectParser
    {
        private readonly bool m_constructed;

        internal DLTaggedObjectParser(int tagClass, int tagNo, bool constructed, Asn1StreamParser parser)
            : base(tagClass, tagNo, parser)
        {
            m_constructed = constructed;
        }

        public override bool IsConstructed
        {
            get { return m_constructed; }
        }

        public override IAsn1Convertible ParseBaseUniversal(bool declaredExplicit, int baseTagNo)
        {
            if (declaredExplicit)
            {
                if (!m_constructed)
                    throw new IOException("Explicit tags must be constructed (see X.690 8.14.2)");

                return m_parser.ParseObject(baseTagNo);
            }

            return m_constructed
                ?  m_parser.ParseImplicitConstructedDL(baseTagNo)
                :  m_parser.ParseImplicitPrimitive(baseTagNo);
        }

        public override IAsn1Convertible ParseExplicitBaseObject()
        {
            if (!m_constructed)
                throw new IOException("Explicit tags must be constructed (see X.690 8.14.2)");

            return m_parser.ReadObject();
        }

        public override Asn1TaggedObjectParser ParseExplicitBaseTagged()
        {
            if (!m_constructed)
                throw new IOException("Explicit tags must be constructed (see X.690 8.14.2)");

            return m_parser.ParseTaggedObject();
        }

        public override Asn1TaggedObjectParser ParseImplicitBaseTagged(int baseTagClass, int baseTagNo)
        {
            return new DLTaggedObjectParser(baseTagClass, baseTagNo, m_constructed, m_parser);
        }

        public override Asn1Object ToAsn1Object()
		{
			try
			{
                return m_parser.LoadTaggedDL(TagClass, TagNo, m_constructed);
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

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DLTaggedObjectParser.cs`.

**Classes defined**: DLTaggedObjectParser

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 61
- Comment lines: 3
- Blank lines: 11

### Main Components

**Classes** (1):
- `DLTaggedObjectParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

