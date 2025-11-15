# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DerOctetString.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DerOctetString.cs`
- **Size**: 1,796 bytes
- **Lines**: 59
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1
{
    public class DerOctetString
        : Asn1OctetString
    {
		/// <param name="contents">The octets making up the octet string.</param>
        public DerOctetString(byte[] contents)
			: base(contents)
        {
        }

        public DerOctetString(IAsn1Convertible obj)
            : this(obj.ToAsn1Object())
        {
        }

        public DerOctetString(Asn1Encodable obj)
            : base(obj.GetEncoded(Der))
        {
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            return new PrimitiveEncoding(Asn1Tags.Universal, Asn1Tags.OctetString, contents);
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            return new PrimitiveEncoding(tagClass, tagNo, contents);
        }

        internal static void Encode(Asn1OutputStream asn1Out, byte[] buf, int off, int len)
		{
            asn1Out.WriteIdentifier(Asn1Tags.Universal, Asn1Tags.OctetString);
            asn1Out.WriteDL(len);
            asn1Out.Write(buf, off, len);
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        internal static void Encode(Asn1OutputStream asn1Out, ReadOnlySpan<byte> buf)
        {
            asn1Out.WriteIdentifier(Asn1Tags.Universal, Asn1Tags.OctetString);
            asn1Out.WriteDL(buf.Length);
            asn1Out.Write(buf);
        }

        internal static void Encode(Asn1OutputStream asn1Out, ReadOnlySpan<byte> buf1, ReadOnlySpan<byte> buf2)
        {
            asn1Out.WriteIdentifier(Asn1Tags.Universal, Asn1Tags.OctetString);
            asn1Out.WriteDL(buf1.Length + buf2.Length);
            asn1Out.Write(buf1);
            asn1Out.Write(buf2);
        }
#endif
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DerOctetString.cs`.

**Classes defined**: DerOctetString



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 47
- Comment lines: 3
- Blank lines: 9

### Main Components

**Classes** (1):
- `DerOctetString`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

