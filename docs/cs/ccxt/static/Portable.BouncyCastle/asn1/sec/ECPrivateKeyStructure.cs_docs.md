# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/sec/ECPrivateKeyStructure.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/sec/ECPrivateKeyStructure.cs`
- **Size**: 3,528 bytes
- **Lines**: 128
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Asn1;
using Org.BouncyCastle.Math;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.Sec
{
    /**
     * the elliptic curve private key object from SEC 1
     */
    public class ECPrivateKeyStructure
        : Asn1Encodable
    {
        private readonly Asn1Sequence seq;

        public static ECPrivateKeyStructure GetInstance(object obj)
        {
            if (obj == null)
                return null;
            if (obj is ECPrivateKeyStructure)
                return (ECPrivateKeyStructure)obj;
            return new ECPrivateKeyStructure(Asn1Sequence.GetInstance(obj));
        }

        private ECPrivateKeyStructure(Asn1Sequence seq)
        {
            if (seq == null)
                throw new ArgumentNullException("seq");

            this.seq = seq;
        }

        public ECPrivateKeyStructure(
            int         orderBitLength,
            BigInteger  key)
            : this(orderBitLength, key, null)
        {
        }

        public ECPrivateKeyStructure(
            int             orderBitLength,
            BigInteger      key,
            Asn1Encodable   parameters)
            : this(orderBitLength, key, null, parameters)
        {
        }

        public ECPrivateKeyStructure(
            int             orderBitLength,
            BigInteger      key,
            DerBitString    publicKey,
            Asn1Encodable   parameters)
        {
            if (key == null)
                throw new ArgumentNullException("key");
            if (orderBitLength < key.BitLength)
                throw new ArgumentException("must be >= key bitlength", "orderBitLength");

            byte[] bytes = BigIntegers.AsUnsignedByteArray((orderBitLength + 7) / 8, key);

            Asn1EncodableVector v = new Asn1EncodableVector(
                new DerInteger(1),
                new DerOctetString(bytes));

            if (parameters != null)
            {
                v.Add(new DerTaggedObject(true, 0, parameters));
            }

            if (publicKey != null)
            {
                v.Add(new DerTaggedObject(true, 1, publicKey));
            }

            this.seq = new DerSequence(v);
        }

        public virtual BigInteger GetKey()
        {
            Asn1OctetString octs = (Asn1OctetString) seq[1];

            return new BigInteger(1, octs.GetOctets());
        }

        public virtual DerBitString GetPublicKey()
        {
            return (DerBitString) GetObjectInTag(1);
        }

        public virtual Asn1Object GetParameters()
        {
            return GetObjectInTag(0);
        }

        private Asn1Object GetObjectInTag(int tagNo)
        {
            foreach (Asn1Encodable ae in seq)
            {
                Asn1Object obj = ae.ToAsn1Object();

                if (obj is Asn1TaggedObject)
                {
                    Asn1TaggedObject tag = (Asn1TaggedObject) obj;
                    if (tag.TagNo == tagNo)
                    {
                        return tag.GetObject();
                    }
                }
            }

            return null;
        }

        /**
         * ECPrivateKey ::= SEQUENCE {
         *     version INTEGER { ecPrivkeyVer1(1) } (ecPrivkeyVer1),
         *     privateKey OCTET STRING,
         *     parameters [0] Parameters OPTIONAL,
         *     publicKey [1] BIT STRING OPTIONAL }
         */
        public override Asn1Object ToAsn1Object()
        {
            return seq;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/sec/ECPrivateKeyStructure.cs`.

**Classes defined**: ECPrivateKeyStructure

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 128
- Code lines: 106
- Comment lines: 10
- Blank lines: 12

### Main Components

**Classes** (1):
- `ECPrivateKeyStructure`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

