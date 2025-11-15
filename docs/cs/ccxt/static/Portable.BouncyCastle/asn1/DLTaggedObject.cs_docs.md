# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DLTaggedObject.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DLTaggedObject.cs`
- **Size**: 2,395 bytes
- **Lines**: 76
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal class DLTaggedObject
        : DerTaggedObject
    {
        internal DLTaggedObject(int tagNo, Asn1Encodable obj)
            : base(tagNo, obj)
        {
        }

        internal DLTaggedObject(int tagClass, int tagNo, Asn1Encodable obj)
            : base(tagClass, tagNo, obj)
        {
        }

        internal DLTaggedObject(bool isExplicit, int tagNo, Asn1Encodable obj)
            : base(isExplicit, tagNo, obj)
        {
        }

        internal DLTaggedObject(bool isExplicit, int tagClass, int tagNo, Asn1Encodable obj)
            : base(isExplicit, tagClass, tagNo, obj)
        {
        }

        internal DLTaggedObject(int explicitness, int tagClass, int tagNo, Asn1Encodable obj)
            : base(explicitness, tagClass, tagNo, obj)
        {
        }

        internal override string Asn1Encoding
        {
            // TODO[asn1] Use DL encoding when supported
            get { return Ber; }
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            if (Asn1OutputStream.EncodingDer == encoding)
                return base.GetEncoding(encoding);

            Asn1Object baseObject = GetBaseObject().ToAsn1Object();

            if (!IsExplicit())
                return baseObject.GetEncodingImplicit(encoding, TagClass, TagNo);

            return new ConstructedDLEncoding(TagClass, TagNo, new IAsn1Encoding[]{ baseObject.GetEncoding(encoding) });
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            if (Asn1OutputStream.EncodingDer == encoding)
                return base.GetEncodingImplicit(encoding, tagClass, tagNo);

            Asn1Object baseObject = GetBaseObject().ToAsn1Object();

            if (!IsExplicit())
                return baseObject.GetEncodingImplicit(encoding, tagClass, tagNo);

            return new ConstructedDLEncoding(tagClass, tagNo, new IAsn1Encoding[]{ baseObject.GetEncoding(encoding) });
        }

        internal override Asn1Sequence RebuildConstructed(Asn1Object asn1Object)
        {
            return new DLSequence(asn1Object);
        }

        internal override Asn1TaggedObject ReplaceTag(int tagClass, int tagNo)
        {
            return new DLTaggedObject(explicitness, tagClass, tagNo, obj);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DLTaggedObject.cs`.

**Classes defined**: DLTaggedObject



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 58
- Comment lines: 1
- Blank lines: 17

### Main Components

**Classes** (1):
- `DLTaggedObject`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

