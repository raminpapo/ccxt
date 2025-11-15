# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1UniversalTypes.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1UniversalTypes.cs`
- **Size**: 3,687 bytes
- **Lines**: 75
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal sealed class Asn1UniversalTypes
    {
        private Asn1UniversalTypes()
        {
        }

        internal static Asn1UniversalType Get(int tagNo)
        {
            switch (tagNo)
            {
            case Asn1Tags.Boolean:
                return DerBoolean.Meta.Instance;
            case Asn1Tags.Integer:
                return DerInteger.Meta.Instance;
            case Asn1Tags.BitString:
                return DerBitString.Meta.Instance;
            case Asn1Tags.OctetString:
                return Asn1OctetString.Meta.Instance;
            case Asn1Tags.Null:
                return Asn1Null.Meta.Instance;
            case Asn1Tags.ObjectIdentifier:
                return DerObjectIdentifier.Meta.Instance;
            case Asn1Tags.ObjectDescriptor:         // [UNIVERSAL 7] IMPLICIT GraphicString
                return Asn1ObjectDescriptor.Meta.Instance;
            case Asn1Tags.External:
                return DerExternal.Meta.Instance;
            case Asn1Tags.Enumerated:
                return DerEnumerated.Meta.Instance;
            case Asn1Tags.Utf8String:               // [UNIVERSAL 12] IMPLICIT OCTET STRING (encode as if)
                return DerUtf8String.Meta.Instance;
            case Asn1Tags.RelativeOid:
                return Asn1RelativeOid.Meta.Instance;
            case Asn1Tags.Sequence:
                return Asn1Sequence.Meta.Instance;
            case Asn1Tags.Set:
                return Asn1Set.Meta.Instance;
            case Asn1Tags.NumericString:            // [UNIVERSAL 18] IMPLICIT OCTET STRING (encode as if)
                return DerNumericString.Meta.Instance;
            case Asn1Tags.PrintableString:          // [UNIVERSAL 19] IMPLICIT OCTET STRING (encode as if)
                return DerPrintableString.Meta.Instance;
            case Asn1Tags.T61String:                // [UNIVERSAL 20] IMPLICIT OCTET STRING (encode as if)
                return DerT61String.Meta.Instance;
            case Asn1Tags.VideotexString:           // [UNIVERSAL 21] IMPLICIT OCTET STRING (encode as if)
                return DerVideotexString.Meta.Instance;
            case Asn1Tags.IA5String:                // [UNIVERSAL 22] IMPLICIT OCTET STRING (encode as if)
                return DerIA5String.Meta.Instance;
            case Asn1Tags.UtcTime:                  // [UNIVERSAL 23] IMPLICIT VisibleString (restricted values)
                return DerUtcTime.Meta.Instance;
            case Asn1Tags.GeneralizedTime:          // [UNIVERSAL 24] IMPLICIT VisibleString (restricted values)
                return DerGeneralizedTime.Meta.Instance;
            case Asn1Tags.GraphicString:            // [UNIVERSAL 25] IMPLICIT OCTET STRING (encode as if)
                return DerGraphicString.Meta.Instance;
            case Asn1Tags.VisibleString:            // [UNIVERSAL 26] IMPLICIT OCTET STRING (encode as if)
                return DerVisibleString.Meta.Instance;
            case Asn1Tags.GeneralString:            // [UNIVERSAL 27] IMPLICIT OCTET STRING (encode as if)
                return DerGeneralString.Meta.Instance;
            case Asn1Tags.UniversalString:          // [UNIVERSAL 28] IMPLICIT OCTET STRING (encode as if)
                return DerUniversalString.Meta.Instance;
            case Asn1Tags.BmpString:                // [UNIVERSAL 30] IMPLICIT OCTET STRING (encode as if)
                return DerBmpString.Meta.Instance;

            case Asn1Tags.Real:
            case Asn1Tags.EmbeddedPdv:
            case Asn1Tags.UnrestrictedString:
            default:
                return null;
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1UniversalTypes.cs`.

**Classes defined**: Asn1UniversalTypes



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 71
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `Asn1UniversalTypes`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

