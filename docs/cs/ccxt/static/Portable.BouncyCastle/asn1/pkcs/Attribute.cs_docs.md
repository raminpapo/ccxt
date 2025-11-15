# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/Attribute.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/Attribute.cs`
- **Size**: 1,969 bytes
- **Lines**: 80
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.Pkcs
{
    public class AttributePkcs
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier attrType;
        private readonly Asn1Set attrValues;

		/**
         * return an Attribute object from the given object.
         *
         * @param o the object we want converted.
         * @exception ArgumentException if the object cannot be converted.
         */
        public static AttributePkcs GetInstance(
            object obj)
        {
            AttributePkcs attr = obj as AttributePkcs;
            if (obj == null || attr != null)
            {
                return attr;
            }

			Asn1Sequence seq = obj as Asn1Sequence;
            if (seq != null)
            {
                return new AttributePkcs(seq);
            }

			throw new ArgumentException("Unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		private AttributePkcs(
            Asn1Sequence seq)
        {
			if (seq.Count != 2)
				throw new ArgumentException("Wrong number of elements in sequence", "seq");

			attrType = DerObjectIdentifier.GetInstance(seq[0]);
            attrValues = Asn1Set.GetInstance(seq[1]);
        }

		public AttributePkcs(
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

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/Attribute.cs`.

**Classes defined**: AttributePkcs

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 68
- Comment lines: 15
- Blank lines: -3

### Main Components

**Classes** (1):
- `AttributePkcs`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

