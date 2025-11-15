# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x9/X9ECPoint.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x9/X9ECPoint.cs`
- **Size**: 1,787 bytes
- **Lines**: 76
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Org.BouncyCastle.Math.EC;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X9
{
    /**
     * class for describing an ECPoint as a Der object.
     */
    public class X9ECPoint
        : Asn1Encodable
    {
        private readonly Asn1OctetString encoding;

        private ECCurve c;
        private ECPoint p;

        public X9ECPoint(ECPoint p, bool compressed)
        {
            this.p = p.Normalize();
            this.encoding = new DerOctetString(p.GetEncoded(compressed));
        }

        public X9ECPoint(ECCurve c, byte[] encoding)
        {
            this.c = c;
            this.encoding = new DerOctetString(Arrays.Clone(encoding));
        }

        public X9ECPoint(ECCurve c, Asn1OctetString s)
            : this(c, s.GetOctets())
        {
        }

        public byte[] GetPointEncoding()
        {
            return Arrays.Clone(encoding.GetOctets());
        }

        public ECPoint Point
        {
            get
            {
                if (p == null)
                {
                    p = c.DecodePoint(encoding.GetOctets()).Normalize();
                }

                return p;
            }
        }

        public bool IsPointCompressed
        {
            get
            {
                byte[] octets = encoding.GetOctets();
                return octets != null && octets.Length > 0 && (octets[0] == 2 || octets[0] == 3);
            }
        }

        /**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         *  ECPoint ::= OCTET STRING
         * </pre>
         * <p>
         * Octet string produced using ECPoint.GetEncoded().</p>
         */
        public override Asn1Object ToAsn1Object()
        {
            return encoding;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x9/X9ECPoint.cs`.

**Classes defined**: for, X9ECPoint

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 64
- Comment lines: 11
- Blank lines: 1

### Main Components

**Classes** (1):
- `X9ECPoint`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

