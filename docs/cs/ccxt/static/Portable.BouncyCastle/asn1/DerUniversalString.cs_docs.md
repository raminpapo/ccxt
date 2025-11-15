# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/DerUniversalString.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/DerUniversalString.cs`
- **Size**: 5,308 bytes
- **Lines**: 173
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Diagnostics;
using System.IO;
using System.Text;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1
{
    /**
     * UniversalString object.
     */
    public class DerUniversalString
        : DerStringBase
    {
        internal class Meta : Asn1UniversalType
        {
            internal static readonly Asn1UniversalType Instance = new Meta();

            private Meta() : base(typeof(DerUniversalString), Asn1Tags.UniversalString) {}

            internal override Asn1Object FromImplicitPrimitive(DerOctetString octetString)
            {
                return CreatePrimitive(octetString.GetOctets());
            }
        }

        private static readonly char[] table = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F' };

		/**
         * return a universal string from the passed in object.
         *
         * @exception ArgumentException if the object cannot be converted.
         */
        public static DerUniversalString GetInstance(
            object obj)
        {
            if (obj == null || obj is DerUniversalString)
            {
                return (DerUniversalString)obj;
            }
            else if (obj is IAsn1Convertible)
            {
                Asn1Object asn1Object = ((IAsn1Convertible)obj).ToAsn1Object();
                if (asn1Object is DerUniversalString)
                    return (DerUniversalString)asn1Object;
            }
            else if (obj is byte[])
            {
                try
                {
                    return (DerUniversalString)Meta.Instance.FromByteArray((byte[])obj);
                }
                catch (IOException e)
                {
                    throw new ArgumentException("failed to construct universal string from byte[]: " + e.Message);
                }
            }

            throw new ArgumentException("illegal object in GetInstance: " + Platform.GetTypeName(obj));
        }

        /**
         * return a universal string from a tagged object.
         *
         * @param taggedObject the tagged object holding the object we want
         * @param declaredExplicit true if the object is meant to be explicitly tagged false otherwise.
         * @exception ArgumentException if the tagged object cannot be converted.
         */
        public static DerUniversalString GetInstance(Asn1TaggedObject taggedObject, bool declaredExplicit)
        {
            return (DerUniversalString)Meta.Instance.GetContextInstance(taggedObject, declaredExplicit);
        }

        private readonly byte[] m_contents;

        public DerUniversalString(byte[] contents)
            : this(contents, true)
        {
        }

        internal DerUniversalString(byte[] contents, bool clone)
        {
            if (null == contents)
                throw new ArgumentNullException("contents");

            m_contents = clone ? Arrays.Clone(contents) : contents;
        }

        public override string GetString()
        {
            int dl = m_contents.Length;
            int capacity = 3 + 2 * (Asn1OutputStream.GetLengthOfDL(dl) + dl);
            StringBuilder buf = new StringBuilder("#1C", capacity);
            EncodeHexDL(buf, dl);

            for (int i = 0; i < dl; ++i)
            {
                EncodeHexByte(buf, m_contents[i]);
            }

            Debug.Assert(buf.Length == capacity);
            return buf.ToString();
        }

        public byte[] GetOctets()
        {
            return Arrays.Clone(m_contents);
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            return new PrimitiveEncoding(Asn1Tags.Universal, Asn1Tags.UniversalString, m_contents);
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            return new PrimitiveEncoding(tagClass, tagNo, m_contents);
        }

        protected override bool Asn1Equals(Asn1Object asn1Object)
        {
            DerUniversalString that = asn1Object as DerUniversalString;
            return null != that
                && Arrays.AreEqual(this.m_contents, that.m_contents);
        }

        protected override int Asn1GetHashCode()
        {
            return Arrays.GetHashCode(m_contents);
        }

        internal static DerUniversalString CreatePrimitive(byte[] contents)
        {
            return new DerUniversalString(contents, false);
        }

        private static void EncodeHexByte(StringBuilder buf, int i)
        {
            buf.Append(table[(i >> 4) & 0xF]);
            buf.Append(table[i & 0xF]);
        }

        private static void EncodeHexDL(StringBuilder buf, int dl)
        {
            if (dl < 128)
            {
                EncodeHexByte(buf, dl);
                return;
            }

            byte[] stack = new byte[5];
            int pos = 5;

            do
            {
                stack[--pos] = (byte)dl;
                dl >>= 8;
            }
            while (dl != 0);

            int count = stack.Length - pos;
            stack[--pos] = (byte)(0x80 | count);

            do
            {
                EncodeHexByte(buf, stack[pos++]);
            }
            while (pos < stack.Length);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/DerUniversalString.cs`.

**Classes defined**: DerUniversalString, Meta

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 173
- Code lines: 145
- Comment lines: 15
- Blank lines: 13

### Main Components

**Classes** (2):
- `DerUniversalString`
- `Meta`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

