# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/ConstructedILEncoding.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/ConstructedILEncoding.cs`
- **Size**: 1,058 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal class ConstructedILEncoding
        : IAsn1Encoding
    {
        private readonly int m_tagClass;
        private readonly int m_tagNo;
        private readonly IAsn1Encoding[] m_contentsElements;

        internal ConstructedILEncoding(int tagClass, int tagNo, IAsn1Encoding[] contentsElements)
        {
            m_tagClass = tagClass;
            m_tagNo = tagNo;
            m_contentsElements = contentsElements;
        }

        void IAsn1Encoding.Encode(Asn1OutputStream asn1Out)
        {
            asn1Out.WriteIdentifier(Asn1Tags.Constructed | m_tagClass, m_tagNo);
            asn1Out.WriteByte(0x80);
            asn1Out.EncodeContents(m_contentsElements);
            asn1Out.WriteByte(0x00);
            asn1Out.WriteByte(0x00);
        }

        int IAsn1Encoding.GetLength()
        {
            return Asn1OutputStream.GetLengthOfIdentifier(m_tagNo)
                +  3
                +  Asn1OutputStream.GetLengthOfContents(m_contentsElements);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/ConstructedILEncoding.cs`.

**Classes defined**: ConstructedILEncoding



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 31
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `ConstructedILEncoding`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

