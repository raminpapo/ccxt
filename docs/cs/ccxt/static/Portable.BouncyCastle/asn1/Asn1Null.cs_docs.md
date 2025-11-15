# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Null.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Null.cs`
- **Size**: 2,136 bytes
- **Lines**: 76
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
     * A Null object.
     */
    public abstract class Asn1Null
        : Asn1Object
    {
        internal class Meta : Asn1UniversalType
        {
            internal static readonly Asn1UniversalType Instance = new Meta();

            private Meta() : base(typeof(Asn1Null), Asn1Tags.Null) {}

            internal override Asn1Object FromImplicitPrimitive(DerOctetString octetString)
            {
                return CreatePrimitive(octetString.GetOctets());
            }
        }

        public static Asn1Null GetInstance(object obj)
        {
            if (obj == null || obj is Asn1Null)
            {
                return (Asn1Null)obj;
            }
            else if (obj is IAsn1Convertible)
            {
                Asn1Object asn1Object = ((IAsn1Convertible)obj).ToAsn1Object();
                if (asn1Object is Asn1Null)
                    return (Asn1Null)asn1Object;
            }
            else if (obj is byte[])
            {
                try
                {
                    return (Asn1Null)Meta.Instance.FromByteArray((byte[])obj);
                }
                catch (IOException e)
                {
                    throw new ArgumentException("failed to construct NULL from byte[]: " + e.Message);
                }
            }

            throw new ArgumentException("illegal object in GetInstance: " + Platform.GetTypeName(obj));
        }

        public static Asn1Null GetInstance(Asn1TaggedObject taggedObject, bool declaredExplicit)
        {
            return (Asn1Null)Meta.Instance.GetContextInstance(taggedObject, declaredExplicit);
        }

        internal Asn1Null()
        {
        }

        public override string ToString()
        {
            return "NULL";
        }

        internal static Asn1Null CreatePrimitive(byte[] contents)
        {
            if (0 != contents.Length)
                throw new InvalidOperationException("malformed NULL encoding encountered");

            return DerNull.Instance;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Null.cs`.

**Classes defined**: Meta, Asn1Null

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 64
- Comment lines: 3
- Blank lines: 9

### Main Components

**Classes** (2):
- `Asn1Null`
- `Meta`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

