# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/ConstructedDLEncoding.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/ConstructedDLEncoding.cs`
- **Size**: 1,135 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal class ConstructedDLEncoding
        : IAsn1Encoding
    {
        private readonly int m_tagClass;
        private readonly int m_tagNo;
        private readonly IAsn1Encoding[] m_contentsElements;
        private readonly int m_contentsLength;

        internal ConstructedDLEncoding(int tagClass, int tagNo, IAsn1Encoding[] contentsElements)
        {
            m_tagClass = tagClass;
            m_tagNo = tagNo;
            m_contentsElements = contentsElements;
            m_contentsLength = Asn1OutputStream.GetLengthOfContents(contentsElements);
        }

        void IAsn1Encoding.Encode(Asn1OutputStream asn1Out)
        {
            asn1Out.WriteIdentifier(Asn1Tags.Constructed | m_tagClass, m_tagNo);
            asn1Out.WriteDL(m_contentsLength);
            asn1Out.EncodeContents(m_contentsElements);
        }

        int IAsn1Encoding.GetLength()
        {
            return Asn1OutputStream.GetLengthOfIdentifier(m_tagNo)
                +  Asn1OutputStream.GetLengthOfDL(m_contentsLength)
                +  m_contentsLength;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/ConstructedDLEncoding.cs`.

**Classes defined**: ConstructedDLEncoding



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 31
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `ConstructedDLEncoding`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

