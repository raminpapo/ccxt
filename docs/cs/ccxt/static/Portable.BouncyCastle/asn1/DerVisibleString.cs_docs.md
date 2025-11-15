# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DerVisibleString.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DerVisibleString.cs`
- **Size**: 4,080 bytes
- **Lines**: 132
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1
{
    /**
     * VisibleString object.
     */
    public class DerVisibleString
        : DerStringBase
    {
        internal class Meta : Asn1UniversalType
        {
            internal static readonly Asn1UniversalType Instance = new Meta();

            private Meta() : base(typeof(DerVisibleString), Asn1Tags.VisibleString) {}

            internal override Asn1Object FromImplicitPrimitive(DerOctetString octetString)
            {
                return CreatePrimitive(octetString.GetOctets());
            }
        }

        /**
         * return a visible string from the passed in object.
         *
         * @exception ArgumentException if the object cannot be converted.
         */
        public static DerVisibleString GetInstance(
            object obj)
        {
            if (obj == null || obj is DerVisibleString)
            {
                return (DerVisibleString)obj;
            }
            else if (obj is IAsn1Convertible)
            {
                Asn1Object asn1Object = ((IAsn1Convertible)obj).ToAsn1Object();
                if (asn1Object is DerVisibleString)
                    return (DerVisibleString)asn1Object;
            }
            else if (obj is byte[])
            {
                try
                {
                    return (DerVisibleString)Meta.Instance.FromByteArray((byte[])obj);
                }
                catch (IOException e)
                {
                    throw new ArgumentException("failed to construct visible string from byte[]: " + e.Message);
                }
            }

            throw new ArgumentException("illegal object in GetInstance: " + Platform.GetTypeName(obj));
        }

        /**
         * return a visible string from a tagged object.
         *
         * @param taggedObject the tagged object holding the object we want
         * @param declaredExplicit true if the object is meant to be explicitly tagged false otherwise.
         * @exception ArgumentException if the tagged object cannot be converted.
         */
        public static DerVisibleString GetInstance(Asn1TaggedObject taggedObject, bool declaredExplicit)
        {
            return (DerVisibleString)Meta.Instance.GetContextInstance(taggedObject, declaredExplicit);
        }

        private readonly byte[] m_contents;

        public DerVisibleString(string str)
        {
			if (str == null)
				throw new ArgumentNullException("str");

			m_contents = Strings.ToAsciiByteArray(str);
        }

        public DerVisibleString(byte[] contents)
            : this(contents, true)
        {
        }

        internal DerVisibleString(byte[] contents, bool clone)
        {
            if (null == contents)
                throw new ArgumentNullException("contents");

            m_contents = clone ? Arrays.Clone(contents) : contents;
        }

        public override string GetString()
        {
            return Strings.FromAsciiByteArray(m_contents);
        }

		public byte[] GetOctets()
        {
            return Arrays.Clone(m_contents);
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            return new PrimitiveEncoding(Asn1Tags.Universal, Asn1Tags.VisibleString, m_contents);
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            return new PrimitiveEncoding(tagClass, tagNo, m_contents);
        }

        protected override bool Asn1Equals(Asn1Object asn1Object)
        {
            DerVisibleString that = asn1Object as DerVisibleString;
            return null != that
                && Arrays.AreEqual(this.m_contents, that.m_contents);
        }

        protected override int Asn1GetHashCode()
        {
            return Arrays.GetHashCode(m_contents);
        }

        internal static DerVisibleString CreatePrimitive(byte[] contents)
        {
            return new DerVisibleString(contents, false);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DerVisibleString.cs`.

**Classes defined**: Meta, DerVisibleString

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 132
- Code lines: 111
- Comment lines: 15
- Blank lines: 6

### Main Components

**Classes** (2):
- `DerVisibleString`
- `Meta`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

