# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Attribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Attribute.cs`
- **Size**: 1,981 bytes
- **Lines**: 83
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
    public class AttributeX509
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier	attrType;
        private readonly Asn1Set				attrValues;

		/**
         * return an Attr object from the given object.
         *
         * @param o the object we want converted.
         * @exception ArgumentException if the object cannot be converted.
         */
        public static AttributeX509 GetInstance(
            object obj)
        {
            if (obj == null || obj is AttributeX509)
            {
                return (AttributeX509) obj;
            }

			if (obj is Asn1Sequence)
            {
                return new AttributeX509((Asn1Sequence) obj);
            }

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		private AttributeX509(
            Asn1Sequence seq)
        {
			if (seq.Count != 2)
				throw new ArgumentException("Bad sequence size: " + seq.Count);

			attrType = DerObjectIdentifier.GetInstance(seq[0]);
			attrValues = Asn1Set.GetInstance(seq[1]);
        }

		public AttributeX509(
            DerObjectIdentifier	attrType,
            Asn1Set				attrValues)
        {
            this.attrType = attrType;
            this.attrValues = attrValues;
        }

		public DerObjectIdentifier AttrType
		{
			get { return attrType; }
		}

		public Asn1Encodable[] GetAttributeValues()
		{
			return attrValues.ToArray();
		}

		public Asn1Set AttrValues
		{
			get { return attrValues; }
		}

		/**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         * Attr ::= Sequence {
         *     attrType OBJECT IDENTIFIER,
         *     attrValues Set OF AttributeValue
         * }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
			return new DerSequence(attrType, attrValues);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Attribute.cs`.

**Classes defined**: AttributeX509

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 83
- Code lines: 70
- Comment lines: 15
- Blank lines: -2

### Main Components

**Classes** (1):
- `AttributeX509`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

