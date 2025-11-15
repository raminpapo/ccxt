# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DLBitString.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DLBitString.cs`
- **Size**: 1,407 bytes
- **Lines**: 56
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    /// <summary>A Definite length BIT STRING</summary>
    public class DLBitString
        : DerBitString
    {
        public DLBitString(byte data, int padBits)
            : base(data, padBits)
        {
        }

        public DLBitString(byte[] data)
            : this(data, 0)
        {
        }

        public DLBitString(byte[] data, int padBits)
            : base(data, padBits)
        {
        }

        public DLBitString(int namedBits)
            : base(namedBits)
        {
        }

        public DLBitString(Asn1Encodable obj)
            : this(obj.GetDerEncoded(), 0)
        {
        }

        internal DLBitString(byte[] contents, bool check)
            : base(contents, check)
        {
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            if (Asn1OutputStream.EncodingDer == encoding)
                return base.GetEncoding(encoding);

            return new PrimitiveEncoding(Asn1Tags.Universal, Asn1Tags.BitString, contents);
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            if (Asn1OutputStream.EncodingDer == encoding)
                return base.GetEncodingImplicit(encoding, tagClass, tagNo);

            return new PrimitiveEncoding(tagClass, tagNo, contents);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DLBitString.cs`.

**Classes defined**: DLBitString



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 44
- Comment lines: 1
- Blank lines: 11

### Main Components

**Classes** (1):
- `DLBitString`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

