# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/LazyDLSet.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/LazyDLSet.cs`
- **Size**: 3,082 bytes
- **Lines**: 125
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Collections.Generic;
using System.IO;

namespace Org.BouncyCastle.Asn1
{
    internal class LazyDLSet
        : DLSet
    {
        private byte[] encoded;

        internal LazyDLSet(byte[] encoded)
            : base()
        {
            if (null == encoded)
                throw new ArgumentNullException("encoded");

            this.encoded = encoded;
        }

        public override Asn1Encodable this[int index]
        {
            get
            {
                Force();

                return base[index];
            }
        }

        public override IEnumerator<Asn1Encodable> GetEnumerator()
        {
            byte[] encoded = GetContents();
            if (null != encoded)
                return new LazyDLEnumerator(encoded);

            return base.GetEnumerator();
        }

        public override int Count
        {
            get
            {
                Force();

                return base.Count;
            }
        }

        public override Asn1Encodable[] ToArray()
        {
            Force();

            return base.ToArray();
        }

        public override string ToString()
        {
            Force();

            return base.ToString();
        }

        internal override IAsn1Encoding GetEncoding(int encoding)
        {
            if (Asn1OutputStream.EncodingBer == encoding)
            {
                byte[] encoded = GetContents();
                if (null != encoded)
                    return new ConstructedLazyDLEncoding(Asn1Tags.Universal, Asn1Tags.Set, encoded);
            }
            else
            {
                Force();
            }

            return base.GetEncoding(encoding);
        }

        internal override IAsn1Encoding GetEncodingImplicit(int encoding, int tagClass, int tagNo)
        {
            if (Asn1OutputStream.EncodingBer == encoding)
            {
                byte[] encoded = GetContents();
                if (null != encoded)
                    return new ConstructedLazyDLEncoding(tagClass, tagNo, encoded);
            }
            else
            {
                Force();
            }

            return base.GetEncodingImplicit(encoding, tagClass, tagNo);
        }

        private void Force()
        {
            lock (this)
            {
                if (null != encoded)
                {
                    Asn1InputStream input = new LazyAsn1InputStream(encoded);
                    try
                    {
                        Asn1EncodableVector v = input.ReadVector();

                        this.elements = v.TakeElements();
                        this.isSorted = elements.Length < 2;
                        this.encoded = null;
                    }
                    catch (IOException e)
                    {
                        throw new Asn1ParsingException("malformed ASN.1: " + e.Message, e);
                    }
                }
            }
        }

        private byte[] GetContents()
        {
            lock (this) return encoded;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/LazyDLSet.cs`.

**Classes defined**: LazyDLSet



## Detailed Walkthrough

### Code Structure

- Total lines: 125
- Code lines: 104
- Comment lines: 0
- Blank lines: 21

### Main Components

**Classes** (1):
- `LazyDLSet`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

