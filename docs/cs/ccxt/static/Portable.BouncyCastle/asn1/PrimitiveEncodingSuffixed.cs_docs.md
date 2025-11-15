# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/PrimitiveEncodingSuffixed.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/PrimitiveEncodingSuffixed.cs`
- **Size**: 1,167 bytes
- **Lines**: 37
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal class PrimitiveEncodingSuffixed
        : IAsn1Encoding
    {
        private readonly int m_tagClass;
        private readonly int m_tagNo;
        private readonly byte[] m_contentsOctets;
        private readonly byte m_contentsSuffix;

        internal PrimitiveEncodingSuffixed(int tagClass, int tagNo, byte[] contentsOctets, byte contentsSuffix)
        {
            m_tagClass = tagClass;
            m_tagNo = tagNo;
            m_contentsOctets = contentsOctets;
            m_contentsSuffix = contentsSuffix;
        }

        void IAsn1Encoding.Encode(Asn1OutputStream asn1Out)
        {
            asn1Out.WriteIdentifier(m_tagClass, m_tagNo);
            asn1Out.WriteDL(m_contentsOctets.Length);
            asn1Out.Write(m_contentsOctets, 0, m_contentsOctets.Length - 1);
            asn1Out.WriteByte(m_contentsSuffix);
        }

        int IAsn1Encoding.GetLength()
        {
            return Asn1OutputStream.GetLengthOfIdentifier(m_tagNo)
                +  Asn1OutputStream.GetLengthOfDL(m_contentsOctets.Length)
                +  m_contentsOctets.Length;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/PrimitiveEncodingSuffixed.cs`.

**Classes defined**: PrimitiveEncodingSuffixed



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 32
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `PrimitiveEncodingSuffixed`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

