# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/OtherName.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/OtherName.cs`
- **Size**: 2,204 bytes
- **Lines**: 72
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * The OtherName object.
     * <pre>
     * OtherName ::= SEQUENCE {
     *      type-id    OBJECT IDENTIFIER,
     *      value      [0] EXPLICIT ANY DEFINED BY type-id }
     * </pre>
     */
    public class OtherName
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier typeID;
        private readonly Asn1Encodable value;

        /**
         * OtherName factory method.
         * @param obj the object used to construct an instance of <code>
         * OtherName</code>. It must be an instance of <code>OtherName
         * </code> or <code>ASN1Sequence</code>.
         * @return the instance of <code>OtherName</code> built from the
         * supplied object.
         * @throws java.lang.IllegalArgumentException if the object passed
         * to the factory is not an instance of <code>OtherName</code> or something that
         * can be converted into an appropriate <code>ASN1Sequence</code>.
         */
        public static OtherName GetInstance(object obj)
        {
            if (obj is OtherName)
                return (OtherName)obj;
            if (obj == null)
                return null;
            return new OtherName(Asn1Sequence.GetInstance(obj));
        }

        /**
         * Base constructor.
         * @param typeID the type of the other name.
         * @param value the ANY object that represents the value.
         */
        public OtherName(DerObjectIdentifier typeID, Asn1Encodable value)
        {
            this.typeID = typeID;
            this.value  = value;
        }

        private OtherName(Asn1Sequence seq)
        {
            this.typeID = DerObjectIdentifier.GetInstance(seq[0]);
            this.value = DerTaggedObject.GetInstance(seq[1]).GetObject(); // explicitly tagged
        }

        public virtual DerObjectIdentifier TypeID
        {
            get { return typeID; }
        }

        public Asn1Encodable Value
        {
            get { return value; }
        }

        public override Asn1Object ToAsn1Object()
        {
            return new DerSequence(typeID, new DerTaggedObject(true, 0, value));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/OtherName.cs`.

**Classes defined**: OtherName

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 64
- Comment lines: 24
- Blank lines: -16

### Main Components

**Classes** (1):
- `OtherName`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

